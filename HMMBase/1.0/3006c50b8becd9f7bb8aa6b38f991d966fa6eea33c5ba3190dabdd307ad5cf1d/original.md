```
posteriors(hmm, observations; robust) -> Vector
```

Compute posterior probabilities using samples likelihoods.

**Example**

```julia
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
y = rand(hmm, 1000)
γ = posteriors(hmm, y)
```
