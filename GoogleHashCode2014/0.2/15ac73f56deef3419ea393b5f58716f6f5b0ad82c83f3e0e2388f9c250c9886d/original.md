```
random_walk(rng::Random.AbstractRNG, city::City)
random_walk(city:::City)
```

Compute and return a [`Solution`](@ref) from `city` by letting each car follow a random walk from its starting point.

!!! tip
    You can pass a random number generator with a specific seed, like `Random.MersenneTwister(0)`, to obtain reproducible results. Otherwise, the global random number generator will be used, and the results will be different for every run.


# Example

```jldoctest
julia> using GoogleHashCode2014, Random

julia> city = read_city();

julia> rng = Random.MersenneTwister(0);

julia> solution = random_walk(rng, city)
Solution with 8 itineraries of lengths [3810, 3277, 3779, 3278, 3451, 3697, 4366, 3707]
```
