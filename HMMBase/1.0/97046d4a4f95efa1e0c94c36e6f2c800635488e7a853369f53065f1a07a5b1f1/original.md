```
rand([rng, ]hmm, T; init, seq) -> Array | (Vector, Array)
```

Sample a trajectory of `T` timesteps from `hmm`.

**Keyword Arguments**

  * `init::Integer = rand(Categorical(hmm.a))`: initial state.
  * `seq::Bool = false`: whether to return the hidden state sequence or not.

**Output**

  * `Vector{Int}` (if `seq == true`): hidden state sequence.
  * `Vector{Float64}` (for `Univariate` HMMs): observations (`T`).
  * `Matrix{Float64}` (for `Multivariate` HMMs): observations (`T x dim(obs)`).

**Examples**

```julia
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
y = rand(hmm, 1000) # or
z, y = rand(hmm, 1000, seq = true)
size(y) # (1000,)
```

```julia
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [MvNormal(ones(2)), MvNormal(ones(2))])
y = rand(hmm, 1000) # or
z, y = rand(hmm, 1000, seq = true)
size(y) # (1000, 2)
```
