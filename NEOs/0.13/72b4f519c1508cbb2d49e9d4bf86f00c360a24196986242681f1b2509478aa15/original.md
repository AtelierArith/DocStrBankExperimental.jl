```
read_observatories_mpc(s::String)
```

Return the matches of `NEOs.OBSERVATORY_MPC_REGEX` in `s` as `Vector{ObservatoryMPC{Float64}}`. `s` can be either a filename or a text.
