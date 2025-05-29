```
recursive_merge_timesteps(x::T, y::U)::promote_type(T,U) where {T<: AbstractVector,U<: AbstractVector}
```

helper function to recursively merge timestep vectors (e.g., of dictionaries)
