```
find_occupied_mode(::SingleComponentFockAddress, k)
find_occupied_mode(::BoseFS, k, [n])
```

Find the `k`-th occupied mode in address (with at least `n` particles). Returns [`BoseFSIndex`](@ref) for [`BoseFS`](@ref), and [`FermiFSIndex`](@ref) for [`FermiFS`](@ref). When unsuccessful it returns a zero index.

# Example

```jldoctest
julia> find_occupied_mode(FermiFS(1, 1, 1, 0), 2)
FermiFSIndex(occnum=1, mode=2, offset=1)

julia> find_occupied_mode(BoseFS(1, 0, 2), 1)
BoseFSIndex(occnum=1, mode=1, offset=0)

julia> find_occupied_mode(BoseFS(1, 0, 2), 1, 2)
BoseFSIndex(occnum=2, mode=3, offset=3)
```

See also [`occupied_modes`](@ref), [`OccupiedModeMap`](@ref), [`SingleComponentFockAddress`](@ref).
