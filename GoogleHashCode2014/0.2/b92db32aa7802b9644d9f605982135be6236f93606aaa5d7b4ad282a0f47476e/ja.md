```
change_duration(city::City, total_duration::Integer)
```

新しい[`City`](@ref)を返し、`total_duration`が異なり、他のすべてのフィールドは`city`のものと等しいです。

# 例

```jldoctest
julia> using GoogleHashCode2014

julia> city = read_city()
City with 11348 junctions and 17958 streets.
8 cars all start from junction 4517 and travel for at most 54000s.

julia> change_duration(city, 3600)
City with 11348 junctions and 17958 streets.
8 cars all start from junction 4517 and travel for at most 3600s.
```
