```
setparameters!(agent, parameters)
```

Assign agent's parameters. Parameters are accepted in the form of a dictionary containing `path => params` pairs.

# Examples

```julia
setparameters!(agent, Dict("agent1/agent2" => Dict(:α=>1)))
```
