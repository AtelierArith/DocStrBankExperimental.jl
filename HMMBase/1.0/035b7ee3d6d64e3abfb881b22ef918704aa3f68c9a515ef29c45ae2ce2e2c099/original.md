```
rand([rng, ]hmm, z) -> Array
```

Sample observations from `hmm` according to trajectory `z`.

**Output**

  * `Vector{Float64}` (for `Univariate` HMMs): observations (`T`).
  * `Matrix{Float64}` (for `Multivariate` HMMs): observations (`T x dim(obs)`).

**Example**

```julia
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
y = rand(hmm, [1, 1, 2, 2, 1])
```
