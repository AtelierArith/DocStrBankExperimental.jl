```
get_scaling_fit(merit_scaling::MeritScaling; precision::Real = 1e-2)
get_scaling_fit(merits::Vector{Merit}, dist_range::Vector{Int}; precision::Real = 1e-2)
```

Returns merit scaling fit data as a [`ScalingFit`](@ref) object for the merit scaling data `merits` fit against the distances `dist_range`, contained in the scaling data `merit_scaling`, displaying a warning if data is not fit to relative precision `precision`.
