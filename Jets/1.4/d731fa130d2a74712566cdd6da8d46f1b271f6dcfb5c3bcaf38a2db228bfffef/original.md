```
lhs,rhs = dot_product_test(A, m, d; mmask, dmask)
```

Compute and return the left and right hand sides of the *dot product test*:

`<d,Am> ≈ <Aᴴd,m>`

Here `Aᴴ` is the conjugate transpose or adjoint of `A`, and `<x, y>` denotes the inner product of vectors `x` and `y`. The left and right hand sides of the dot product test are expected to be equivalent close to machine precision for operator `A`. If the equality does not hold this can indicate a problem with the implementation of the operator `A`.

This function provides the optional named arguments `mmask` and `dmask` which are vectors in the domain and range of `A` that are applied via elementwise multiplication to mask the vectors `m` and `d` before applying of the operator, as shown below. Here we use `∘` to represent the Hadamard product (elementwise multiplication) of two vectors.

`<dmask ∘ d, A (mmask ∘ m)> ≈ <Aᵀ (dmask ∘ d), mmask ∘ m>`

You can test the relative accuracy of the operator with this relation for the left hand side `lhs` and right hand side `rhs` returned by this function: 

`|lhs - rhs| / |lhs + rhs| < ϵ`
