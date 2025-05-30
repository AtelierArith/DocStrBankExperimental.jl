```
a, ai = action_info(policy, x)
```

Return a tuple containing the action determined by policy 'p' at state or belief 'x' and information (usually a `NamedTuple`, `Dict` or `nothing`) from the calculation of that action.

By default, returns `nothing` as info.
