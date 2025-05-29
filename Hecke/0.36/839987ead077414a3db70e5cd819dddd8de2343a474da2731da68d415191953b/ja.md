```
root_lattice(R::Vector{Tuple{Symbol,Int}}) -> ZZLat
```

型 `R` のルート格子を返します（[`root_lattice`](@ref)を参照）。

#例

```jldoctest
julia> root_lattice([(:A,2),(:A,1)])
ランク3および次数3の整数格子
グラム行列
[ 2   -1   0]
[-1    2   0]
[ 0    0   2]

```
