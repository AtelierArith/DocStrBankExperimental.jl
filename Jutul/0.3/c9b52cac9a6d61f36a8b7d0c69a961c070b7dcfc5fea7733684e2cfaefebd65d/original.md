```
simulator_config(sim; info_level = 3, linear_solver = GenericKrylov())
```

Set up a simulator configuration object that can be passed onto [`simulate!`](@ref).

There are many options available to configure a given simulator. The best way to get an overview of these possible configuration options is to instatiate the config without any arguments and inspecting the resulting table by calling `simulator_config(sim)` in the REPL.
