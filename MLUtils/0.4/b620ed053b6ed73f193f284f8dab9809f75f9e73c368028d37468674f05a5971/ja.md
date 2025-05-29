```
obsview(data::AbstractArray, [obsdim])
obsview(data::AbstractArray, idxs, [obsdim])
```

与えられたインデックス `idxs` に対応する配列 `data` のビューを返します。もし [`ObsDim`](@ref) 型の `obsdim` が提供されている場合、配列の観測次元はその次元に沿っていると仮定されます。そうでない場合は、最後の次元であると仮定されます。

`idxs` が提供されていない場合、`1:numobs(data)` であると仮定されます。

# 例

```jldoctest
julia> x = rand(4, 5, 2);

julia> v = obsview(x, 2:3, ObsDim(2));

julia> numobs(v)
2

julia> getobs(v, 1) == x[:, 2, :]
true

julia> getobs(v, 1:2) == x[:, 2:3, :]
true
```
