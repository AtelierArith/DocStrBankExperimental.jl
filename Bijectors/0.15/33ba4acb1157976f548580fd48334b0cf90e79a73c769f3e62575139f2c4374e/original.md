```
isclosedform(b::Transform)::bool
isclosedform(b⁻¹::Inverse{<:Transform})::bool
```

Returns `true` or `false` depending on whether or not evaluation of `b` has a closed-form implementation.

Most transformations have closed-form evaluations, but there are cases where this is not the case. For example the *inverse* evaluation of `PlanarLayer` requires an iterative procedure to evaluate.
