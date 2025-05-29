```
×(v::PVector, w::PVector...)
```

[`combine`](@ref) の演算子バージョンです。

## 例

```julia
julia> v = PVector([1, 2, 3]);
julia> w = PVector([4, 5]);
julia> v × w
[1 : 2 : 3] × [4 : 5]
```
