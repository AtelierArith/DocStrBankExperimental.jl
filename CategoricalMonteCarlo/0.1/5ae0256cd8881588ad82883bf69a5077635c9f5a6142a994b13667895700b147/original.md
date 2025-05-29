```
sample!(B::AbstractArray, A::AbstractArray)
```

Draw samples, summing (and potentially reducing) in-place into `B`. The shape of `B` determines the extent of reduction performed.

See also: [`tsample!`](@ref), [`vsample!`](@ref), [`vtsample!`](@ref)
