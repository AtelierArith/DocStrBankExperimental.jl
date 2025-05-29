```
is_street(i::Integer, j::Integer, street::Street)
```

Check if the trip from junction index `i` to junction index `j` corresponds to a valid direction of `street`.

The valid directions for a [`Street`](@ref) are:

  * from `street.endpointA` to `street.endpointB` in every case
  * from `street.endpointB` to `street.endpointA` only if `street.bidirectional` is `true`

# Example

```jldoctest
julia> using GoogleHashCode2014

julia> city = read_city(); 

julia> street = city.streets[10]
Bidirectional street between junction indices 6814 and 2728 - duration 13s, distance 187m

julia> is_street(1, 2728, street)
false

julia> is_street(6814, 2728, street)
true

julia> is_street(2728, 6814, street)
true

julia> street = city.streets[11]
Monodirectional street from junction index 3779 to index 7853 - duration 12s, distance 88m

julia> is_street(3779, 7853, street)
true

julia> is_street(7853, 3779, street)  # because it is not bidirectional
false
```
