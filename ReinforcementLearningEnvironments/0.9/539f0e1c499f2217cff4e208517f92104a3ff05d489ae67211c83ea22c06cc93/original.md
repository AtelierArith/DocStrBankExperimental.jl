```
StateTransformedEnv(env; state_mapping=identity, state_space_mapping=identity)
```

`state_mapping` will be applied on the original state when calling `state(env)`, and similarly `state_space_mapping` will be applied when calling `state_space(env)`.
