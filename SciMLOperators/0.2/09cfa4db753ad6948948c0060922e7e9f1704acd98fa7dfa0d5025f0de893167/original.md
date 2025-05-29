```julia
⊗(ops)

```

Computes the lazy pairwise Kronecker product, or tensor product, operator of `AbstractMatrix`, and `AbstractSciMLOperator` subtypes. Calling `⊗(ops...)` is equivalent to `Base.kron(ops...)`. Fast operator evaluation is performed without forming the full tensor product operator.

```
TensorProductOperator(A, B) = A ⊗ B
TensorProductOperator(A, B, C) = A ⊗ B ⊗ C

(A ⊗ B)(u) = vec(B * reshape(u, M, N) * transpose(A))
```

where `M = size(B, 2)`, and `N = size(A, 2)`
