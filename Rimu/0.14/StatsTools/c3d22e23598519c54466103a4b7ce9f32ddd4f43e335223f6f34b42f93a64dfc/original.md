```
val_and_errs(x; n=1, p=nothing, name=:val) -> (;val, val_l, val_u)
```

Return the median and the lower and upper error bar for the uncertain value `x` as a `NamedTuple`. This is useful for plotting scripts. The interval `[val - val_l, val + val_u]` represents the confidence interval at level `n*σ`, or at probability `p`. Setting `p` overrides `n`. Supports  [`MonteCarloMeasurements`](https://github.com/baggepinnen/MonteCarloMeasurements.jl) and [`Measurements`](https://github.com/JuliaPhysics/Measurements.jl). The  names in the `NamedTuple` can be changed with `name`.

**Example:**

```jldoctest
julia> results = [blocking_analysis(i:0.1:2i+20) for i in 1:3]; # mock results

julia> v = val_and_errs.(results, name="res"); # Vector of NamedTuple's with standard errors

julia> DataFrame(v)
3×3 DataFrame
 Row │ res      res_l    res_u
     │ Float64  Float64  Float64
─────┼───────────────────────────
   1 │    11.5  1.7282   1.7282
   2 │    13.0  1.7282   1.7282
   3 │    14.5  1.78885  1.78885
```

See [`NamedTuple`](@ref), [`val`](@ref), [`errs`](@ref), [`BlockingResult`](@ref), [`RatioBlockingResult`](@ref).
