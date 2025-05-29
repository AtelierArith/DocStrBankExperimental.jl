```
..(a, b)
a .. b
```

Create the interval $[a, b]$ according to the IEEE Standard 1788-2015. This is semantically equivalent to [`interval(a, b)`](@ref).

!!! danger
    Nothing is done to compensate for the fact that floating point literals are rounded to the nearest when parsed (e.g. `0.1`). In such cases, parse the string containing the desired value to ensure its tight enclosure.


See also: [`interval`](@ref), [`±`](@ref) and [`@I_str`](@ref).

# Examples

```jldoctest
julia> using IntervalArithmetic

julia> using IntervalArithmetic.Symbols

julia> setdisplay(:full);

julia> (1//1)..π
Interval{Rational{Int64}}(1//1, 85563208//27235615, com)

julia> 0.1..0.3
Interval{Float64}(0.1, 0.3, com)
```
