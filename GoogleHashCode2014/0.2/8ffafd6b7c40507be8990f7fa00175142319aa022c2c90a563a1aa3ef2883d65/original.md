```
is_feasible(solution::Solution, city::City; verbose::Bool=false)
```

Check if `solution` satisfies the constraints for the instance defined by `city`.

The following criteria are considered (taken from the problem statement):

  * the number of itineraries has to match the number of cars of `city`
  * the first junction of each itinerary has to be the starting junction of `city`
  * for each consecutive pair of junctions on an itinerary, a street connecting these junctions has to exist in `city` (if the street is one directional, it has to be traversed in the correct direction)
  * the duration of each itinerary has to be lower or equal to the total duration of `city`

# Example

```jldoctest
julia> using GoogleHashCode2014, Random

julia> city = read_city();

julia> rng = Random.MersenneTwister(0);

julia> solution = random_walk(rng, city)
Solution with 8 itineraries of lengths [3810, 3277, 3779, 3278, 3451, 3697, 4366, 3707]

julia> is_feasible(solution, city; verbose=false)
true

julia> partial_solution = Solution(solution.itineraries[1:7])
Solution with 7 itineraries of lengths [3810, 3277, 3779, 3278, 3451, 3697, 4366]

julia> is_feasible(partial_solution, city; verbose=false)
false
```
