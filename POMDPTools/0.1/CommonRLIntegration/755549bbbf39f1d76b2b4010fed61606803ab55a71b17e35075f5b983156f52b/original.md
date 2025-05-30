```
POMDPCommonRLEnv(m, [s], [o])
POMDPCommonRLEnv{RLO}(m, [s], [o])
```

Create a CommonRLInterface environment from POMDP m; optionally specify the state 's' and observation 'o'.

The `RLO` and `RLS` parameters can be used to specify types to convert the observation and state to. By default, this is `AbstractArray`. Use `Any` to disable conversion.
