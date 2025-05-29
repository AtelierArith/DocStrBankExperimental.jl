```
function agent_actions(m::JointMDP, idx::Int64, s::S) where S
```

Returns the discrete actions for the given agent index.

!!! note
    This will be called a LOT so it should not allocate each time....

