```julia
generate_custom_function(sys::AbstractSystem, exprs, dvs = unknowns(sys),
                         ps = parameters(sys); kwargs...)
```

Generate a function to evaluate `exprs`. `exprs` is a symbolic expression or array of symbolic expression involving symbolic variables in `sys`. The symbolic variables may be subsetted using `dvs` and `ps`. All `kwargs` are passed to the internal [`build_function`](@ref) call. The returned function can be called as `f(u, p, t)` or `f(du, u, p, t)` for time-dependent systems and `f(u, p)` or `f(du, u, p)` for time-independent systems. If `split=true` (the default) was passed to [`complete`](@ref), [`structural_simplify`](@ref) or [`@mtkbuild`](@ref), `p` is expected to be an `MTKParameters` object.
