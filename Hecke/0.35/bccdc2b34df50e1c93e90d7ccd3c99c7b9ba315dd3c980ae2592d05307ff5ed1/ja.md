```
restrict(f::NumFieldEmb, K::NumField)
```

数体 $L$ の埋め込み $f$ と、$L$ の基底体として現れる数体 $K$ が与えられたとき、$K$ への $f$ の制限を返します。

# 例

```jldoctest
julia> K, a = quadratic_field(3);

julia> L, b = number_field(polynomial(K, [1, 0, 1]), "b");

julia> e = complex_embeddings(L);

julia> restrict(e[1], K)
Complex embedding corresponding to -1.73
  of real quadratic field defined by x^2 - 3
```
