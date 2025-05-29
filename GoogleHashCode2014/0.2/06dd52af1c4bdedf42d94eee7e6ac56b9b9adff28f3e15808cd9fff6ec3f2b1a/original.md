```
City
```

Store a city made of [`Junction`](@ref)s and [`Street`](@ref)s, along with additional instance parameters.

A `City` object can be constructed with the function [`read_city`](@ref).

# Fields

  * `total_duration::Int`: total time allotted for the car itineraries (in seconds)
  * `nb_cars::Int`: number of cars in the fleet
  * `starting_junction::Int`: index of the junction at which all the cars are located initially (the index refers to a position in the list of junctions)
  * `junctions::Vector{Junction}`: list of junctions
  * `streets::Vector{Street}`: list of streets

# Example

```jldoctest
julia> using GoogleHashCode2014

julia> city = read_city()
City with 11348 junctions and 17958 streets.
8 cars all start from junction 4517 and travel for at most 54000s.
    
julia> length(city.junctions)
11348
    
julia> length(city.streets)
17958

julia> city.starting_junction
4517

julia> city.junctions[10]  # get the junction object at junction index 10
Junction at coordinates (48.872250900000004, 2.3124588)

julia> city.streets[10]  # get the street object at street index 10
Bidirectional street between junction indices 6814 and 2728 - duration 13s, distance 187m
```
