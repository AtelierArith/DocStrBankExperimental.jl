```
add_agent!([pos,] [MicrobeType,] model; kwargs...)
```

MicrobeAgents extension of `Agents.add_agent!`. Creates and adds a new microbe to `model`, using the constructor of the agent type of the model. If `model` accepts mixed agent types, then `MicrobeType` must be specified. If not specified, `pos` will be assigned randomly in the model domain.

Keywords can be used to specify default values to pass to the microbe constructor, otherwise default values from the constructor will be used. If unspecified, a random velocity vector and a random speed are generated.
