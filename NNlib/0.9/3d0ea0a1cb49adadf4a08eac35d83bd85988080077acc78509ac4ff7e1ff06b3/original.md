```
make_causal_mask(x, dims=2)
```

Return a boolean square matrix `m` of the same type as `x` and of side `size(x, dims)`. Its elements are set such that `m[i, j] == i ≤ j`.

Can be used to mask the attention scores in [`dot_product_attention`](@ref).
