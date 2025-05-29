```
GradientConfig(f::Polynomial{T}, [x::AbstractVector{S}])
```

A data structure with which the gradient of a `Polynomial` `f` can be evaluated efficiently. Note that `x` is only used to determine the output type of `f(x)`.

```
GradientConfig(f::Polynomial{T}, [S])
```

Instead of a vector `x` a type can also be given directly.
