```
getobservable(agent, args...)
```

Get agent's observable.

# Examples

```julia
getobservable(getagent(agent, "../model"), "observable_name")
getobservable(getagent(agent, "../model"), 1)
```
