```
ActionTransformedEnv(env;action_space_mapping=identity, action_mapping=identity)
```

`action_space_mapping` will be applied to `action_space(env)` and `legal_action_space(env)`. `action_mapping` will be applied to `action` before feeding it into `env`.
