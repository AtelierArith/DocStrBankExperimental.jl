```
optimal_algorithm(dim, stepsize, eps=stepsize^(3/2), norm=MaxL2())
optimal_algorithm(dim, q_12, stepsize, eps, norm=FrobeniusL2())
```

Returns the optimal algorithm for the given parameters, i.e. the algorithm that needs to simulate the fewest random numbers to achieve the desired precision `eps`.

# Examples

```jldoctest; setup=:(using LevyArea)
julia> h = 1/128;

julia> optimal_algorithm(10, h, h^(3/2), MaxL2())
MronRoe()

julia> optimal_algorithm(10, 1.0./(1:10).^2, h, h^(3/2), FrobeniusL2())
Milstein()
```
