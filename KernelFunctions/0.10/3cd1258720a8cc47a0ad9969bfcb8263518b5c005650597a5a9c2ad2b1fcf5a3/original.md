```
with_lengthscale(kernel::Kernel, lengthscales::AbstractVector{<:Real})
```

Construct a transformed "ARD" kernel with different `lengthscales` for each dimension.

# Examples

```jldoctest
julia> kernel = with_lengthscale(SqExponentialKernel(), [0.5, 2.5]);

julia> x = rand(2);

julia> y = rand(2);

julia> kernel(x, y) ≈ (SqExponentialKernel() ∘ ARDTransform([2, 0.4]))(x, y)
true
```
