```
RandomPolicy(action_space=nothing; rng=Random.default_rng())
```

If `action_space` is `nothing`, then it will use the `legal_action_space` at runtime to randomly select an action. Otherwise, a random element within `action_space` is selected.

!!! note
    You should always set `action_space=nothing` when dealing with environments of `FULL_ACTION_SET`.

