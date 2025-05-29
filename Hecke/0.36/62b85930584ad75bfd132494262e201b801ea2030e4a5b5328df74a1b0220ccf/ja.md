```
extend(e::NumFieldEmb, f::NumFieldHom)
```

埋め込み $e$ と射影 $f \colon k \to K$ が与えられたとき、$f$ に沿って $e$ に制限される $K$ のすべての埋め込みを決定します。

# 例

```jldoctest
julia> K, a = cyclotomic_field(5, "a");

julia> k, ktoK = Hecke.subfield(K, [a + inv(a)]);

julia> e = complex_embeddings(k)[1];

julia> extend(e, ktoK)
2-element Vector{AbsSimpleNumFieldEmbedding}:
 Imaginary embedding with -0.81 + 0.59 * i of K
 Imaginary embedding with -0.81 - 0.59 * i of K
```
