```
TabularApproximator(table<:AbstractArray)
```

For `table` of 1-d, it will serve as a state value approximator. For `table` of 2-d, it will serve as a state-action value approximator.

!!! warning
    For `table` of 2-d, the first dimension is action and the second dimension is state.

