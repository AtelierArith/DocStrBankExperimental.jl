lorenz(v)

Compute the relative Lorenz Curve of a vector `v` . 

Returns two vectors. The first one contains the cumulative proportion of people.  The second contains the cumulative share of income earned.

# Examples

```julia
julia> using Inequality
julia> lorenz_curve([8, 5, 1, 3, 5, 6, 7, 6, 3])
([0.0, 0.1111111111111111, 0.2222222222222222, 0.3333333333333333, 0.4444444444444444, 0.5555555555555556, 0.6666666666666666, 0.7777777777777778, 0.8888888888888888, 1.0], 
│ [0.0, 0.022727272727272728, 0.09090909090909091, 0.1590909090909091, 0.2727272727272727, 0.38636363636363635, 0.5227272727272727, 0.6590909090909091, 0.8181818181818182, 1.0])
```
