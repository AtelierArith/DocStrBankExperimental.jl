```
find_occupied_mode(::SingleComponentFockAddress, k)
find_occupied_mode(::BoseFS, k, [n])
```

アドレス内の `k` 番目の占有モードを見つけます（少なくとも `n` 粒子を持つ）。[`BoseFS`](@ref) には [`BoseFSIndex`](@ref) を、[`FermiFS`](@ref) には [`FermiFSIndex`](@ref) を返します。失敗した場合はゼロインデックスを返します。

# 例

```jldoctest
julia> find_occupied_mode(FermiFS(1, 1, 1, 0), 2)
FermiFSIndex(occnum=1, mode=2, offset=1)

julia> find_occupied_mode(BoseFS(1, 0, 2), 1)
BoseFSIndex(occnum=1, mode=1, offset=0)

julia> find_occupied_mode(BoseFS(1, 0, 2), 1, 2)
BoseFSIndex(occnum=2, mode=3, offset=3)
```

[`occupied_modes`](@ref)、[`OccupiedModeMap`](@ref)、[`SingleComponentFockAddress`](@ref) も参照してください。
