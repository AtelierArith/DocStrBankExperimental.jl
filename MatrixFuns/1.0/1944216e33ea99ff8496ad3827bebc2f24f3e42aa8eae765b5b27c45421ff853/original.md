```
div_diff(f, x::AbstractVector; kwargs...)
div_diff(f, x::Tuple; kwargs...)
div_diff(f, x...; kwargs...)
```

Return the divided difference `f[x_0,x_1,...,x_n]`, assuming `f` is called as `f(x)`.  See `mat_fun` for a description of possible keyword arguments.
