```
s_t_connectivity(source::Vector{Int}, target::Vector{Int})
```

Returns a function (system::Matrix{Float64}, components::BitVector) which will evaluate to true if a path from any of the *source* nodes to any of the *target* nodes exists in *system* with only the *components* in working state.
