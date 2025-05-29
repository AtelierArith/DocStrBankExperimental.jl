```
radius(x)
```

Radius of `x`, such that `issubset_interval(x, mid(x) ± radius(x))`. If `x` is complex, then the radius is the maximum radius between its real and imaginary parts.

Implement the `rad` function of the IEEE Standard 1788-2015 (Table 9.2).

See also: [`inf`](@ref), [`sup`](@ref), [`bounds`](@ref), [`mid`](@ref), [`diam`](@ref) and [`midradius`](@ref).
