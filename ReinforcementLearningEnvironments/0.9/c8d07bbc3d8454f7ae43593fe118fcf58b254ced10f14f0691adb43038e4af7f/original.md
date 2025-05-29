```
discrete2standard_discrete(env)
```

Convert an `env` with a discrete action space to a standard form:

  * The action space is of type `Base.OneTo`
  * If the `env` is of `FULL_ACTION_SET`, then each action in the `legal_action_space(env)` is also an `Int` in the action space.

The standard form is useful for some algorithms (like Q-learning).
