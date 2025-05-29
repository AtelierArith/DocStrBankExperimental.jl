```
normal(mean :: Interval, std :: Interval)
```

Normal shaped pbox. Parameters can be Real or Intervals.

# Constructors

  * `normal`
  * `N`
  * `gaussian`

# Examples

```jldoctest
julia> a = normal(interval(0, 1), interval(1,2))
Pbox: 	  ~ normal ( range=[-6.1805, 7.1805], mean=[0.0, 1.0], var=[1.0, 4.0])
```

See also: [`uniform`](@ref), [`lognormal`](@ref), [`meanMinMax`](@ref), [`plot`](@ref)
