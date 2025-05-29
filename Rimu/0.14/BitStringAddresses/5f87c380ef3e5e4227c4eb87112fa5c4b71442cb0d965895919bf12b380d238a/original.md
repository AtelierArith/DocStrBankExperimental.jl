```
OccupiedPairsMap(addr::SingleComponentFockAddress) <: AbstractVector
```

Get a map of all distinct pairs of indices in `addr`. Pairs involving multiply-occupied modes are counted once, (including self-pairing). This is useful for cases where identifying pairs of particles for eg. interactions is not well-defined or efficient to do on the fly. This is an eager iterator whose elements are a tuple of particle indices that can be given to `excitation`

# Example

```jldoctest
julia> addr = BoseFS(10, 0, 0, 0, 2, 0, 1)
BoseFS{13,7}(10, 0, 0, 0, 2, 0, 1)

julia> pairs = OccupiedPairsMap(addr)
5-element OccupiedPairsMap{78, Tuple{BoseFSIndex, BoseFSIndex}}:
 (BoseFSIndex(occnum=10, mode=1, offset=0), BoseFSIndex(occnum=10, mode=1, offset=0))
 (BoseFSIndex(occnum=2, mode=5, offset=14), BoseFSIndex(occnum=2, mode=5, offset=14))
 (BoseFSIndex(occnum=2, mode=5, offset=14), BoseFSIndex(occnum=10, mode=1, offset=0))
 (BoseFSIndex(occnum=1, mode=7, offset=18), BoseFSIndex(occnum=10, mode=1, offset=0))
 (BoseFSIndex(occnum=1, mode=7, offset=18), BoseFSIndex(occnum=2, mode=5, offset=14))

julia> excitation(addr, pairs[2], pairs[4])
(BoseFS{13,7}(9, 0, 0, 0, 4, 0, 0), 10.954451150103322)
```

See also [`OccupiedModeMap`](@ref).
