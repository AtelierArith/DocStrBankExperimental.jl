```
Solution
```

Store a list of itineraries through a [`City`](@ref), one for each car in.

A naive `Solution` can be computed with the function [`random_walk`](@ref).

# Fields

  * `itineraries::Vector{Vector{Int}}`: each itinerary is a vector of junction indices

# Example

```jldoctest
julia> using GoogleHashCode2014, Random

julia> city = read_city();

julia> rng = Random.MersenneTwister(0);

julia> solution = random_walk(rng, city)
Solution with 8 itineraries of lengths [3810, 3277, 3779, 3278, 3451, 3697, 4366, 3707]

julia> length(solution.itineraries[2])  # number of junctions visited by car nb 2
3277

julia> solution.itineraries[2][1:10]  # first 10 junction indices visited by car nb 2
10-element Vector{Int64}:
  4517
  1033
  3656
  7681
   398
  4680
 10361
 10089
 10361
 10089
```
