```
distance(A::Union{Vector{GeoLocation}, GeoLocation, Vector{<:Node}, Node, Vector{<:AbstractFloat}},
         B::Union{Vector{GeoLocation}, GeoLocation, Vector{<:Node}, Node, Vector{<:AbstractFloat}},
         type::Symbol=:haversine
         )
```

Calculates the distance (km) between two points or two vectors of points.

# Arguments

  * `A::Union{Vector{GeoLocation}, GeoLocation, Vector{<:Node}, Node, Vector{<:AbstractFloat}}`: Vector of origin points.
  * `B::Union{Vector{GeoLocation}, GeoLocation, Vector{<:Node}, Node, Vector{<:AbstractFloat}}`: Vector of destination points.
  * `method::Symbol=:haversine`: Either `:haversine` or `:euclidean`.

# Return

  * Distance between origin and destination points in km.
