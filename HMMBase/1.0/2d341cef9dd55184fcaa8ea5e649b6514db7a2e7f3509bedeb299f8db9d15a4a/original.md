```
loglikelihoods(hmm, observations; robust) -> Matrix
```

Return the log-likelihood per-state and per-observation.

**Output**

  * `Matrix{Float64}`: log-likelihoods matrix (`T x K`).

**Example**

```julia
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
y = rand(hmm, 1000)
LL = likelihoods(hmm, y)
```
