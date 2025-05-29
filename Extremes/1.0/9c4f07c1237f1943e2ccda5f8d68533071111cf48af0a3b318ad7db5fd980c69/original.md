```
returnlevelplotci(fm::AbstractFittedExtremeValueModel, α::Real=.05)
```

Return level plot along with the confidence/credible interval of level `1-α`.

## Note

This function is currently only available for stationary models.

See also [`returnlevelplotci`](@ref) and [`qqplot`](@ref).   

## Example

```@example
using Distributions, Extremes

pd = GeneralizedExtremeValue(0,1,0)
y = rand(pd, 300)
fm = gevfit(y)

returnlevelplotci(fm)
```
