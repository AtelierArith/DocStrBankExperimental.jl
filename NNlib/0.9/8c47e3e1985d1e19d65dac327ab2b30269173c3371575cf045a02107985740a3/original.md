```
bias_act!(σ, x, b)
```

This is equivalent to `x .= σ.(x .+ b)`, also replacing `sigmoid` & `tanh` with `sigmoid_fast` & `tanh_fast`. It will only overwrite `x` when `x isa StridedArray{<:AbstractFloat}`.

When used within a gradient, it will overwrite only when `σ` has a method of `derivatives_given_output` which does not need the input at all. Such methods are defined by e.g. `@scalar_rule relu(x) Ω > 0` where the derivative contains only `Ω` (the output) not `x`.

!!! warning
    This is not safe to use if `x` is still needed for the gradient of some other function. Incorrect use will give silently wrong answers. It is intended mainly for Flux layers, in which the previous operation is known to be safe, e.g. `bias_act!(σ, weight * input, bias)` for a `Dense` layer.

