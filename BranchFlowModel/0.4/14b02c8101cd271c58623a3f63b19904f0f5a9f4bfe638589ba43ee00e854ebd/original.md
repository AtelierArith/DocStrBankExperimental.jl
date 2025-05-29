```
set_inputs!(mg::MetaGraphsNext.MetaGraph; α::Float64=0.0)
```

Set the shared values in each subgraph / vertex of mg:

1. set the current vertex's v0 to its inneighbor's voltage
2. set the current vertex P/Qload to the outneighbors' substation_bus loads
