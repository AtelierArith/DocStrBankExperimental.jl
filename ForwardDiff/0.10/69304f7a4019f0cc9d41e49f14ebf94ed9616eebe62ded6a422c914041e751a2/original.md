```
ForwardDiff.gradient(f, x::AbstractArray, cfg::GradientConfig = GradientConfig(f, x), check=Val{true}())
```

Return `∇f` evaluated at `x`, assuming `f` is called as `f(x)`. The array `∇f` has the same shape as `x`, and its elements are `∇f[j, k, ...] = ∂f/∂x[j, k, ...]`.

This method assumes that `isa(f(x), Real)`.

Set `check` to `Val{false}()` to disable tag checking. This can lead to perturbation confusion, so should be used with care.
