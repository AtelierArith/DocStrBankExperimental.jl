```
occupied_modes(::SingleComponentFockAddress)
```

Return a lazy iterator over all occupied modes in an address. Iterates over [`BoseFSIndex`](@ref)s for [`BoseFS`](@ref), and over [`FermiFSIndex`](@ref)s for [`FermiFS`](@ref). See [`OccupiedModeMap`](@ref) for an eager version.

# Example

```jldoctest
julia> b = BoseFS((1,5,0,4));

julia> foreach(println, occupied_modes(b))
BoseFSIndex(occnum=1, mode=1, offset=0)
BoseFSIndex(occnum=5, mode=2, offset=2)
BoseFSIndex(occnum=4, mode=4, offset=9)
```

```jldoctest
julia> f = FermiFS((1,1,0,1,0,0,1));

julia> foreach(println, occupied_modes(f))
FermiFSIndex(occnum=1, mode=1, offset=0)
FermiFSIndex(occnum=1, mode=2, offset=1)
FermiFSIndex(occnum=1, mode=4, offset=3)
FermiFSIndex(occnum=1, mode=7, offset=6)
```

See also [`find_occupied_mode`](@ref), [`SingleComponentFockAddress`](@ref).
