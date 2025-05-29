```
get_street_end(i::Integer, street::Street)
```

Retrieve the junction index at the other end `street` when it is crossed starting from junction index `i`.

If `i` is not a valid starting point for `street`, an error is thrown.

# Example

```jldoctest
julia> using GoogleHashCode2014

julia> city = read_city();

julia> street = city.streets[10]
Bidirectional street between junction indices 6814 and 2728 - duration 13s, distance 187m

julia> get_street_end(6814, street)
2728

julia> get_street_end(2728, street)
6814

julia> street = city.streets[11]
Monodirectional street from junction index 3779 to index 7853 - duration 12s, distance 88m

julia> get_street_end(3779, street)
7853
```
