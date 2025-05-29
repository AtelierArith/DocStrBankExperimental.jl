```
gen_entropy(v, w, α)
```

Compute the Generalized Entropy Index of a vector `v`, using weights given by a weight vector `w`  at a specified parameter `α`.

Weights must not be negative, missing or NaN. The weights and data vectors must have the same length.

# Examples

```julia
julia> using Inequality
julia> gen_entropy([8, 5, 1, 3, 5, 6, 7, 6, 3], collect(0.1:0.1:0.9), 2)
0.0709746654322026
```
