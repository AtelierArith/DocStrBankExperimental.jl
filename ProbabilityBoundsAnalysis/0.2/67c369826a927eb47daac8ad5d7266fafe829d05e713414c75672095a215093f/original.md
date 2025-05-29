```
beta(α :: Interval, β :: Interval)
```

Beta shaped pbox. Parameters can be Real or Intervals.

# Examples

```jldoctest
julia> a = beta(2,interval(3,4))
Pbox: 	  ~ beta ( range=[0.0, 1.0], mean=[0.33333, 0.4], var=[0.031746, 0.04])
```

See also: [`KN`](@ref), [`meanMinMax`](@ref), [`plot`](@ref)
