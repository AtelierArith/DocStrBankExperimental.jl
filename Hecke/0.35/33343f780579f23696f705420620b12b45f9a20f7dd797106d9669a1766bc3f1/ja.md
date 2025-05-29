```
sign(x::NumFieldElem, e::NumFieldEmb) -> Int
```

数体要素 `x` と複素埋め込み `e` が与えられたとき、`e(x)` が正、負、またはゼロであるかに応じて `1`、`-1` または `0` を返します。

# 例

```jldoctest
julia> K, a = quadratic_field(3);

julia> e = complex_embedding(K, 1.7);

julia> sign(a, e)
1
```
