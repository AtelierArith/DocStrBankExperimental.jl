```julia
function invert(state::State{R}) where {R}
```

Given a `State` containing the configuration of `B` with respect to `A`, returns the state containing the configuration of `A` with respect to `B`.
