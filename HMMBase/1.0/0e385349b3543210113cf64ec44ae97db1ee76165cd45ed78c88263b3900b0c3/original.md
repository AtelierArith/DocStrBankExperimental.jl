```
loglikelihood(hmm, observations; robust) -> Float64
```

Compute the log-likelihood of the observations under the model.   This is defined as the sum of the log of the normalization coefficients in the forward filter.

**Output**

  * `Float64`: log-likelihood of the observations sequence under the model.

**Example**

```jldoctest
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
loglikelihood(hmm, [0.15, 0.10, 1.35])
# output
-4.588183811489616
```
