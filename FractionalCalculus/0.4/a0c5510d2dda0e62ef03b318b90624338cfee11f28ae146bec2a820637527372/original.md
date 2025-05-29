# Grünwald Letnikov sense finite difference approximation

```
fracdiff(f::Union{Function, Number}, α::AbstractArray, end_point, h, ::GLFiniteDifference)::Vector
```

Use finite difference method to obtain Grünwald Letnikov sense fractional derivative.

### Example

```julia-repl
julia> fracdiff(x->x, 0.5, 1, 0.01, GLFiniteDifference())
1.1269695801851276
```
