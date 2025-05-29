```
getindex(::ContinuousHistogram, ::Type{<: Moment})
```

Convenience function to access a given [`Moment`](@ref) from its name.

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

julia> hist[FirstMoment]
0.0

julia> hist[SecondMoment]
1.0

julia> hist[ThirdMoment]
0.0

julia> hist[FourthMoment]
3.0
```
