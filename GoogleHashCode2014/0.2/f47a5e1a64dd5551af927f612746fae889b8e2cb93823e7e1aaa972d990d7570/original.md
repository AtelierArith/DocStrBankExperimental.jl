```
is_street_start(i::Integer, street::Street)
```

Check if junction index `i` is a valid starting point of `street`.

# Example

```jldoctest
julia> using GoogleHashCode2014

julia> city = read_city();

julia> street = city.streets[10]
Bidirectional street between junction indices 6814 and 2728 - duration 13s, distance 187m

julia> is_street_start(6814, street)
true

julia> is_street_start(2728, street)
true

julia> street = city.streets[11]
Monodirectional street from junction index 3779 to index 7853 - duration 12s, distance 88m

julia> is_street_start(3779, street)
true

julia> is_street_start(7853, street)
false
```
