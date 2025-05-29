```julia
takestep!(comp)

```

Reads the time `t` from the `trigger` link of `comp`. If `comp` is an `AbstractMemory`, a backward step is taken. Otherwise, a forward step is taken. See also: [`forwardstep`](@ref), [`backwardstep`](@ref).
