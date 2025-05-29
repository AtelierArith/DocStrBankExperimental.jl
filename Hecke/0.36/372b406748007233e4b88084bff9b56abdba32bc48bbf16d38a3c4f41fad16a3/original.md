```
restrict(f::NumFieldEmb, g::NumFieldHom)
```

Given an embedding $f$ of a number field $L$ and a morphism $g \colon K \to L$, return the embedding $g \circ f$ of $K$.

This is the same as `g * f`.

# Examples

```jldoctest
julia> K, a = cyclotomic_field(5, "a");

julia> k, ktoK = Hecke.subfield(K, [a + inv(a)]);

julia> e = complex_embeddings(K);

julia> restrict(e[1], ktoK)
Real embedding
  of number field with defining polynomial x^2 + x - 1
    over rational field
corresponding to root 0.62
```
