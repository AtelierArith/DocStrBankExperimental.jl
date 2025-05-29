```
uniform(min :: Interval, max :: Interval)
```

Uniform shaped pbox. Parameters can be Real or Intervals.

# Constructors

  * `uniform`
  * `U`

# Examples

```jldoctest
julia> a = uniform(interval(0, 1), interval(1,2))
Pbox: 	  ~ uniform ( range=[0.0, 2.0], mean=[0.5, 1.5], var=[0.0, 0.33333])
```

See also: [`normal`](@ref), [`beta`](@ref), [`meanMinMax`](@ref), [`plot`](@ref)
