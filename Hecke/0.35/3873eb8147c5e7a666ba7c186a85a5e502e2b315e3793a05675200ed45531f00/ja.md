```
conj(f::NumFieldEmb) -> NumFieldEmb
```

`f`の共役埋め込みを返します。

# 例

```jldoctest
julia> K, a = quadratic_field(-3); e = complex_embeddings(K);

julia> conj(e[1]) == e[2]
true
```
