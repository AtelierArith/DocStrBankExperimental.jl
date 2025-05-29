```
∇(y::Node{<:∇Scalar})
∇(y::Node{T}, ȳ::T) where T
```

Return a `Tape` object which can be indexed using `Node`s, each element of which contains the result of multiplying `ȳ` by the transpose of the Jacobian of the function specified by the `Tape` object in `y`. If `y` is a scalar and `ȳ = 1` then this is equivalent to computing the gradient of `y` w.r.t. each of the elements in the `Tape`.

```
∇(f::Function, ::Type{Arg{N}}, p, y, ȳ, x...)
```

To implement a new reverse-mode sensitivity for the `N^{th}` argument of function `f`. p is the output of `preprocess`. `x1`, `x2`,... are the inputs to the function, `y` is its output and `ȳ` the reverse-mode sensitivity of `y`.

```
∇(x̄, f::Function, ::Type{Arg{N}}, p, y, ȳ, x...)
```

This is the optional in-place version of `∇` that should, if implemented, mutate x̄ to have the gradient added to it.
