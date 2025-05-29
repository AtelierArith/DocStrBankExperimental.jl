```
combine(v::PVector, w::PVector...)
```

射影ベクトル `v` と `wᵢ` をフラットな積に結合します。演算子バージョンもあり、[`×`](@ref)（`imes<tab>`と書かれます）。

## 例

```julia
julia> v = PVector([1, 2, 3]);
julia> w = PVector([4, 5]);
julia> combine(v, w)
[1 : 2 : 3] × [4 : 5]
```
