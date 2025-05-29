```
extend(e::NumFieldEmb, f::NumFieldHom)
```

Given an embedding $e$ of $k$ and a morphism $f \colon k \to K$, determine all embedings of $K$ which restrict to $e$ along $f$.

# Example

```jldoctest
julia> K, a = cyclotomic_field(5, "a");

julia> k, ktoK = Hecke.subfield(K, [a + inv(a)]);

julia> e = complex_embeddings(k)[1];

julia> extend(e, ktoK)
2-element Vector{AbsSimpleNumFieldEmbedding}:
 Complex embedding corresponding to -0.81 + 0.59 * i of K
 Complex embedding corresponding to -0.81 - 0.59 * i of K
```
