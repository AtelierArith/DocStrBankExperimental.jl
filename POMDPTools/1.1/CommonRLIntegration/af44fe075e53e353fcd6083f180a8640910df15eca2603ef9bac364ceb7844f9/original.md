```
MDPCommonRLEnv(m, [s])
MDPCommonRLEnv{RLO}(m, [s])
```

Create a CommonRLInterface environment from MDP m; optionally specify the state 's'.

The `RLO` parameter can be used to specify a type to convert the observation to. By default, this is `AbstractArray`. Use `Any` to disable conversion.
