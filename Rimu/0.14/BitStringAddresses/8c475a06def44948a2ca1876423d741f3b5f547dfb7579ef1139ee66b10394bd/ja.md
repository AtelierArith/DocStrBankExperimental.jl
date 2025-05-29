```
near_uniform(BoseFS{N,M}) -> BoseFS{N,M}
```

ボソニックフォック状態を、合計 `N` 粒子で `M` モードのほぼ均一な占有数を持つように作成します。

# 例

```jldoctest
julia> near_uniform(BoseFS{7,5})
BoseFS{7,5}(2, 2, 1, 1, 1)

julia> near_uniform(FermiFS{3,5})
FermiFS{3,5}(1, 1, 1, 0, 0)
```
