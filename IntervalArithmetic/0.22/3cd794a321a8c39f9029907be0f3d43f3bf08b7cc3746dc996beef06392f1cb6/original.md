```
interval(T, a, b, d = com)
```

Create the interval $[a, b]$ according to the IEEE Standard 1788-2015. The validity of the interval is checked by [`is_valid_interval`](@ref): if `true` then an `Interval{T}` is constructed, otherwise an NaI (Not an Interval) is returned.

!!! danger
    Nothing is done to compensate for the fact that floating point literals are rounded to the nearest when parsed (e.g. `0.1`). In such cases, parse the string containing the desired value to ensure its tight enclosure.


See also: [`±`](@ref), [`..`](@ref) and [`@I_str`](@ref).

# Examples

```jldoctest
julia> setdisplay(:full);

julia> interval(1//1, π)
Interval{Rational{Int64}}(1//1, 85563208//27235615, com)

julia> interval(Rational{Int32}, 1//1, π)
Interval{Rational{Int32}}(1//1, 85563208//27235615, com)

julia> interval(1, π)
Interval{Float64}(1.0, 3.1415926535897936, com)

julia> interval(BigFloat, 1, π)
Interval{BigFloat}(1.0, 3.141592653589793238462643383279502884197169399375105820974944592307816406286233, com)
```
