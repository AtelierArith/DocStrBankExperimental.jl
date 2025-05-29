```
@einsum [TensorType] expr
```

Performs tensor computations using the [Einstein summation convention](https://en.wikipedia.org/wiki/Einstein_notation). Since `@einsum` cannot fully infer tensor symmetries, it is possible to annotate the returned tensor type (though this is not checked for correctness). This can help eliminate the computation of the symmetric part, improving performance.

The `expr` can be an anonymous function, in which case the arguments of the anonymous function are treated as free indices. If no arguments are provided, the free indices are inferred based on the order in which they appear from left to right.

# Examples

```jldoctest einsum
julia> A = rand(Mat{3,3});

julia> B = rand(Mat{3,3});

julia> (@einsum C[i,j] := A[j,k] * B[k,i]) ≈ (A * B)'
true

julia> (@einsum c := A[i,j] * A[i,j]) ≈ A ⋅ A
true

julia> (@einsum SymmetricSecondOrderTensor{3} D[i,j] := A[k,i] * A[k,j]) ≈ A' * A
true

julia> (@einsum (i,j) -> A[j,k] * B[k,i]) ≈ (A * B)'
true

julia> (@einsum A[i,j] * A[i,j]) ≈ A ⋅ A
true

julia> (@einsum SymmetricSecondOrderTensor{3} A[k,i] * A[k,j]) ≈ A' * A
true
```
