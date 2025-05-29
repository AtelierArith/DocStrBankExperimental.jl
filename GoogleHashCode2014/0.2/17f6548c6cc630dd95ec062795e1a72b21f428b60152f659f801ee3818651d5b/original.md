```
total_distance(solution::Solution, city::City)
```

Compute the total distance traveled by all itineraries in `solution` based on the street data from `city`.

!!! warning
    Streets visited several times or in both directions are only counted once.


# Example

```jldoctest
julia> using GoogleHashCode2014, Random

julia> city = read_city();

julia> rng = Random.MersenneTwister(0);

julia> solution = random_walk(rng, city)
Solution with 8 itineraries of lengths [3810, 3277, 3779, 3278, 3451, 3697, 4366, 3707]

julia> total_distance(solution, city)
752407
```
