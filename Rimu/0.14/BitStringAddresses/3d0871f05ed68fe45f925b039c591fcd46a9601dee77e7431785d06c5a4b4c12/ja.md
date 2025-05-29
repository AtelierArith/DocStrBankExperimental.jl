```
dot(map::OccupiedModeMap, vec::AbstractVector)
dot(map1::OccupiedModeMap, map2::OccupiedModeMap)
```

モード占有数を [`OccupiedModeMap`](@ref) から抽出するドット積は [`onr`](@ref) に似ています。

```jldoctest
julia> b = BoseFS(10, 0, 0, 0, 2, 0, 1)
BoseFS{13,7}(10, 0, 0, 0, 2, 0, 1)

julia> mb = OccupiedModeMap(b)
3-element OccupiedModeMap{7, BoseFSIndex}:
 BoseFSIndex(occnum=10, mode=1, offset=0)
 BoseFSIndex(occnum=2, mode=5, offset=14)
 BoseFSIndex(occnum=1, mode=7, offset=18)

julia> dot(mb, 1:7)
27

julia> mb⋅(1:7) == onr(b)⋅(1:7)
true
```

さらに [`SingleComponentFockAddress`](@ref) を参照してください。
