```
occupied_modes(::SingleComponentFockAddress)
```

アドレス内のすべての占有モードに対する遅延イテレータを返します。[`BoseFSIndex`](@ref)を[`BoseFS`](@ref)のために、[`FermiFSIndex`](@ref)を[`FermiFS`](@ref)のために反復します。イーガー版については[`OccupiedModeMap`](@ref)を参照してください。

# 例

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

他にも[`find_occupied_mode`](@ref)、[`SingleComponentFockAddress`](@ref)を参照してください。
