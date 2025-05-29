```
dirichlet_beta()
```

Calculates Dirichlet beta function,      [https://en.wikipedia.org/wiki/Dirichlet*beta*function](https://en.wikipedia.org/wiki/Dirichlet_beta_function)

## Arguments

  * $s$ `::Number`: it should work for any type of number, but mainly tested for `Complex{Float64}`

## Examples

```jldoctest; setup = :(using Polylogarithms)
julia> dirichlet_beta(1.5)
0.8645026534612017
```
