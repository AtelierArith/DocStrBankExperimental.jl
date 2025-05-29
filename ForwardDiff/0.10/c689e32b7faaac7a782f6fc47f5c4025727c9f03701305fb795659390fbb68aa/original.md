```
ForwardDiff.derivative(f, x::Real)
```

Return `df/dx` evaluated at `x`, assuming `f` is called as `f(x)`.

This method assumes that `isa(f(x), Union{Real,AbstractArray})`.
