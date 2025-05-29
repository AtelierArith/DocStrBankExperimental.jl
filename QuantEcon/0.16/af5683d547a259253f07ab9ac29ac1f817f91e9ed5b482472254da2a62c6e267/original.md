```
random_markov_chain([rng], n[, k])
```

Return a randomly sampled MarkovChain instance with `n` states, where each state has `k` states with positive transition probability.

# Arguments

  * `rng::AbstractRNG=GLOBAL_RNG` : Random number generator.
  * `n::Integer` : Number of states.
  * `k::Integer=n` : Number of nonzero entries in each column of the matrix. Set to `n` if none specified.

# Returns

  * `mc::MarkovChain` : MarkovChain instance.

# Examples

```julia
julia> using QuantEcon, Random

julia> rng = MersenneTwister(1234);

julia> mc = random_markov_chain(rng, 3);

julia> mc.p
3×3 LinearAlgebra.Transpose{Float64,Array{Float64,2}}:
 0.590845  0.175952   0.233203
 0.460085  0.106152   0.433763
 0.794026  0.0601209  0.145853

julia> mc = random_markov_chain(rng, 3, 2);

julia> mc.p
3×3 LinearAlgebra.Transpose{Float64,Array{Float64,2}}:
 0.0       0.200586  0.799414
 0.701386  0.0       0.298614
 0.753163  0.246837  0.0
```
