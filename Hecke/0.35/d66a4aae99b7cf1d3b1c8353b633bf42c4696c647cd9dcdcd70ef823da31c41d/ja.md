```
is_real(f::NumFieldEmb) -> Bool
```

埋め込みが実数であれば `true` を返します。

# 例

```jldoctest
julia> K, a = quadratic_field(3); e = complex_embeddings(K)[1];

julia> is_real(e)
true
```
