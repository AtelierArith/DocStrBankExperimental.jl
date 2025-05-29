```
KVector{K,T,D,N}
```

次元 `D` の幾何代数において、要素数 `N` の型 `T` の幾何的 `K`-ベクトル。

コンストラクタ `KVector{K,D}(elements...)` と `KVector{K,D}(elements::NTuple)` は、引数から自動的に `T` を推論し、`K` と `D` から `N` を推論します。

# 例

```jldoctest
julia> KVector{1,3}(1.0, 2.0, 3.0)
KVector{1, Float64, 3, 3}(1.0, 2.0, 3.0)

julia> KVector{2,3}(1.0, 2.0, 3.0)
Bivector{Float64, 3, 3}(1.0, 2.0, 3.0)

julia> KVector{4,4}(1.0)
Quadvector{Float64, 4, 1}(1.0)
```
