```
push!(::ContinuousHistogram, ::Tuple{Number, Number})
push!(::ContinuousHistogram, ::Measurement)
push!(::ContinuousHistogram, ::AbstractVector)
push!(::ContinuousHistogram, ::Vector{Measurement})
```

`Base` overload to introduce a new value-error pair into the [`ContinuousHistogram`](@ref). This function also [`_update_moments!`](@ref) in an amortized way to add little overhead.

!!! note
    The `AbstractVector` dispatch is really only meant for `Vector{Tuple{Number, Number}}`;  the latter of which contains no subtypes.

