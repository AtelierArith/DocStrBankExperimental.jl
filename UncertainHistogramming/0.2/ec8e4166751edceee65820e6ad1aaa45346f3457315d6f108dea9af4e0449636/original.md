```
moment(::ContinuousHistogram, ::Type{<: Moment})
```

Convenience wrapper to return a [`Moment`](@ref) from a [`ContinuousHistogram`](@ref)  by that [`Moment`](@ref)'s name.

```jldoctest
julia> hist = GaussianHistogram();

julia> push!(hist, (0, 1))
GaussianHistogram{Float64}:
  length  = 1
  moments = 0.0  1.0  0.0  3.0  

  Statistics
    mean        = 0.0
    variance    = 1.0
    skewness    = 0.0
    kurtosis    = 0.0

julia> moment(hist, FirstMoment)
0.0

julia> moment(hist, SecondMoment)
1.0

julia> moment(hist, ThirdMoment)
0.0

julia> moment(hist, FourthMoment)
3.0
```
