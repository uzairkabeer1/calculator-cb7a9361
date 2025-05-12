
    # LangGraph

## Overview
LangGraph is a graph-based orchestration platform for building stateful AI agent workflows. It offers both a code-first Core library and a hosted SaaS control plane for production deployments.

## Key Features
- **Directed Graphs**: Model complex control and data dependencies via nodes and edges.  
- **State Persistence**: Automatic checkpointing and versioned state management.  
- **Visual Studio**: Drag-and-drop graph editor with live debugging and tracing.  
- **CLI & SDKs**: Command-line tools plus Python/JavaScript SDKs for local dev.  
- **Human-In-Loop**: Pause points for approvals, feedback, or manual data corrections.

## Installation

```bash
pip install langgraph-core
````

To install the hosted platform CLI:

```bash
npm install -g @langgraph/cli
```

## Quickstart

```python
from langgraph import Graph, Node

# Define nodes
load = Node("load_data", handler=lambda ctx: ctx.read("data.csv"))
train = Node("train_model", handler=lambda ctx: train_model(ctx.input))
evaluate = Node("evaluate", handler=lambda ctx: evaluate_model(ctx.model))

# Build graph
g = Graph(name="ml-pipeline")
g.add_edge(load, train)
g.add_edge(train, evaluate)

# Run locally
g.run()
```

## Configuration

```jsonc
// langgraph.json
{
  "state_store": "s3://my-bucket/langgraph-state",
  "logging": { "level": "DEBUG" },
  "human_loop": { "timeout_seconds": 3600 }
}
```

## Documentation & Support

* Core docs: [https://docs.langgraph.com/core](https://docs.langgraph.com/core)
* Platform portal: [https://app.langgraph.com](https://app.langgraph.com)
* GitHub: [https://github.com/langgraph/langgraph](https://github.com/langgraph/langgraph)
* License: MIT
    