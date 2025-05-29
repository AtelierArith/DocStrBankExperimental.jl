```
legal_action_space_mask(env, player=current_player(env)) -> AbstractArray{Bool}
```

Required for environments of [`FULL_ACTION_SET`](@ref). As a default implementation,      [`legal_action_space_mask`](@ref) creates a mask of [`action_space`](@ref) with      the subset [`legal_action_space`](@ref).
