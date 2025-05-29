```
kernel ∘ transform
∘(kernel, transform)
compose(kernel, transform)
```

Compose a `kernel` with a transformation `transform` of its inputs.

The prefix forms support chains of multiple transformations: `∘(kernel, transform1, transform2) = kernel ∘ transform1 ∘ transform2`.

# Definition

For inputs $x, x'$, the transformed kernel $\widetilde{k}$ derived from kernel $k$ by input transformation $t$ is defined as

$$
\widetilde{k}(x, x'; k, t) = k\big(t(x), t(x')\big).
$$

# Examples

```jldoctest
julia> (SqExponentialKernel() ∘ ScaleTransform(0.5))(0, 2) == exp(-0.5)
true

julia> ∘(ExponentialKernel(), ScaleTransform(2), ScaleTransform(0.5))(1, 2) == exp(-1)
true
```

See also: [`TransformedKernel`](@ref)
