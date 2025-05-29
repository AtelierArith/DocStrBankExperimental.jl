```
with_lengthscale(kernel::Kernel, lengthscales::AbstractVector{<:Real})
```

異なる次元ごとに異なる `lengthscales` を持つ変換された "ARD" カーネルを構築します。

# 例

```jldoctest
julia> kernel = with_lengthscale(SqExponentialKernel(), [0.5, 2.5]);

julia> x = rand(2);

julia> y = rand(2);

julia> kernel(x, y) ≈ (SqExponentialKernel() ∘ ARDTransform([2, 0.4]))(x, y)
true
```
