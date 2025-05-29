```
randtransmat([rng, ]K, α = 1.0) -> Matrix{Float64}
```

Generate a transition matrix where each row is sampled from a Dirichlet distribution of dimension `K` and concentration parameter `α`.

**Arguments**

  * `K::Integer`: number of states.
  * `α::Float64 = 1.0`: concentration parameter of the Dirichlet distribution.

**Example**

```julia
A = randtransmat(4)
```
