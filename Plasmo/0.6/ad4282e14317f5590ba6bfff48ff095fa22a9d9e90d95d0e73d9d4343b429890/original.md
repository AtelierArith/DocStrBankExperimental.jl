```
graph_backend(graph::OptiGraph)
```

Return the intermediate backend used to map the optigraph to an optimizer. Plasmo.jl  currently only supports a backend to MathOptInterface.jl optimizers, but future versions intend to support GraphOptInterface.jl as a structured backend. 
