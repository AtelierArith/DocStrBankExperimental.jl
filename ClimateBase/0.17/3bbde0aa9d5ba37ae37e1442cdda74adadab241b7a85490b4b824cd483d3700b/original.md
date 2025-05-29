```
temporalranges(A::ClimArray, f = Dates.month) → r
temporalranges(t::AbstractVector{<:TimeType}}, f = Dates.month) → r
```

Return a vector of ranges so that each range of indices are values of `t` that belong in either the same month, year, day, or season, depending on `f`. `f` can take the values: `Dates.year, Dates.month, Dates.day` or `season` (all are functions).

Used in e.g. [`monthlyagg`](@ref), [`yearlyagg`](@ref) or [`seasonalyagg`](@ref).
