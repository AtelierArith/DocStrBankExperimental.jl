```
find_mode(::SingleComponentFockAddress, i)
```

Find the `i`-th mode in address. Returns [`BoseFSIndex`](@ref) for [`BoseFS`](@ref), and [`FermiFSIndex`](@ref) for [`FermiFS`](@ref). Can work on a tuple of modes. Does not check bounds.

```jldoctest
julia> find_mode(BoseFS(1, 0, 2), 2)
BoseFSIndex(occnum=0, mode=2, offset=2)

julia> find_mode(FermiFS(1, 1, 1, 0), (2,3))
(FermiFSIndex(occnum=1, mode=2, offset=1), FermiFSIndex(occnum=1, mode=3, offset=2))
```

See [`SingleComponentFockAddress`](@ref).
