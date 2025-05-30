```
RLEnvPOMDP(env; discount=1.0)
```

Create an `POMDP` by wrapping a `CommonRLInterface.AbstractEnv`. `state` and `setstate!` from `CommonRLInterface` must be provided, and the `POMDPs` generative model functionality will be provided.
