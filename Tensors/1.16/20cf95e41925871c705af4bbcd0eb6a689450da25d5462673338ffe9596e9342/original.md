```
otimes(::Vec, ::Vec)
otimes(::SecondOrderTensor, ::SecondOrderTensor)
```

Compute the open product between two tensors. The symbol `⊗`, written `\otimes`, is overloaded for tensor products.

# Examples

```jldoctest
julia> A = rand(SymmetricTensor{2, 2});

julia> B = rand(SymmetricTensor{2, 2});

julia> A ⊗ B
2×2×2×2 SymmetricTensor{4, 2, Float64, 9}:
[:, :, 1, 1] =
 0.291503  0.490986
 0.490986  0.19547

[:, :, 2, 1] =
 0.115106  0.193876
 0.193876  0.0771855

[:, :, 1, 2] =
 0.115106  0.193876
 0.193876  0.0771855

[:, :, 2, 2] =
 0.128518  0.216466
 0.216466  0.086179
```
