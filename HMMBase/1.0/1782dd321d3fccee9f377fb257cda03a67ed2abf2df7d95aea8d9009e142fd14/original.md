```
forward(hmm, observations; robust) -> (Vector, Float)
```

Compute forward probabilities of the `observations` given the `hmm` model.

**Output**

  * `Vector{Float64}`: forward probabilities.
  * `Float64`: log-likelihood of the observed sequence.

**Example**

```julia
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
y = rand(hmm, 1000)
probs, tot = forward(hmm, y)
```
