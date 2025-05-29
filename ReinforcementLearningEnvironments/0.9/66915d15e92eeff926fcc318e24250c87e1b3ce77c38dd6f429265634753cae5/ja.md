```
ActionTransformedEnv(env;action_space_mapping=identity, action_mapping=identity)
```

`action_space_mapping` は `action_space(env)` と `legal_action_space(env)` に適用されます。 `action_mapping` は `action` に適用され、`env` に渡される前に処理されます。
