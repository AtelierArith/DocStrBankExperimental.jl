```
SignTest(x::AbstractVector{T<:Real}, median::Real = 0)
SignTest(x::AbstractVector{T<:Real}, y::AbstractVector{T<:Real}, median::Real = 0)
```

Perform a sign test of the null hypothesis that the distribution from which `x` (or `x - y` if `y` is provided) was drawn has median `median` against the alternative hypothesis that the median is not equal to `median`.

Implements: [`pvalue`](@ref), [`confint`](@ref)
