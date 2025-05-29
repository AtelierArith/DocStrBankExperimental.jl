```
with_lengthscale(kernel::Kernel, lengthscale::Real)
```

Construct a transformed kernel with `lengthscale`.

# Examples

```jldoctest
julia> kernel = with_lengthscale(SqExponentialKernel(), 2.5);

julia> x = rand(2);

julia> y = rand(2);

julia> kernel(x, y) ≈ (SqExponentialKernel() ∘ ScaleTransform(0.4))(x, y)
true
```
