```
OccupiedModeMap(addr) <: AbstractVector
```

Get a map of occupied modes in address as an `AbstractVector` of indices compatible with [`excitation`](@ref) - [`BoseFSIndex`](@ref) or [`FermiFSIndex`](@ref).

`OccupiedModeMap(addr)[i]` contains the index for the `i`-th occupied mode. This is useful because repeatedly looking for occupied modes with [`find_occupied_mode`](@ref) can be time-consuming. `OccupiedModeMap(addr)` is an eager version of the iterator returned by [`occupied_modes`](@ref). It is similar to [`onr`](@ref) but contains more information.

# Example

```jldoctest
julia> b = BoseFS(10, 0, 0, 0, 2, 0, 1)
BoseFS{13,7}(10, 0, 0, 0, 2, 0, 1)

julia> mb = OccupiedModeMap(b)
3-element OccupiedModeMap{7, BoseFSIndex}:
 BoseFSIndex(occnum=10, mode=1, offset=0)
 BoseFSIndex(occnum=2, mode=5, offset=14)
 BoseFSIndex(occnum=1, mode=7, offset=18)

julia> f = FermiFS(1,1,1,1,0,0,1,0,0)
FermiFS{5,9}(1, 1, 1, 1, 0, 0, 1, 0, 0)

julia> mf = OccupiedModeMap(f)
5-element OccupiedModeMap{5, FermiFSIndex}:
 FermiFSIndex(occnum=1, mode=1, offset=0)
 FermiFSIndex(occnum=1, mode=2, offset=1)
 FermiFSIndex(occnum=1, mode=3, offset=2)
 FermiFSIndex(occnum=1, mode=4, offset=3)
 FermiFSIndex(occnum=1, mode=7, offset=6)

julia> mf == collect(occupied_modes(f))
true

julia> dot(mf, mb)
11

julia> dot(mf, 1:20)
17
```

See also [`dot`](@ref Main.Hamiltonians.dot), [`SingleComponentFockAddress`](@ref).
