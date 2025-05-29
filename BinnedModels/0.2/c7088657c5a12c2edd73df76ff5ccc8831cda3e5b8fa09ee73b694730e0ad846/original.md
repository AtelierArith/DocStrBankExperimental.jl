```
binned_likelihood(f_expectation, edges::Tuple{AbstractVector,...}, data::AbstractVector{<:Integer})
binned_likelihood(f_expectation, h::StatsBase.Histogram{<:Integer})
```

Constructs a binned likelihood object that is compatible with the [DensityInterface](https://github.com/JuliaMath/DensityInterface.jl) API.

See also [`binned_model`](@ref).
