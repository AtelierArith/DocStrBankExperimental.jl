```
smoothed(m::AbstractModel, σ::Number)
```

Smooths a model `m` with a Gaussian kernel with standard deviation `σ`.

# Notes

This uses [`convolved`](@ref) to created the model, i.e.

```julia-repl
julia> convolved(m1, m2) == smoothed(m1, 1.0)
m1 = Disk()
```
