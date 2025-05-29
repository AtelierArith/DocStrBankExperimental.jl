```
restrict(f::NumFieldEmb, g::NumFieldHom)
```

数体 $L$ の埋め込み $f$ と射影 $g \colon K \to L$ が与えられたとき、$K$ の埋め込み $g \circ f$ を返します。

これは `g * f` と同じです。

# 例

```jldoctest
julia> K, a = cyclotomic_field(5, "a");

julia> k, ktoK = Hecke.subfield(K, [a + inv(a)]);

julia> e = complex_embeddings(K);

julia> restrict(e[1], ktoK)
Complex embedding corresponding to 0.62
  of number field with defining polynomial x^2 + x - 1
    over rational field
```
