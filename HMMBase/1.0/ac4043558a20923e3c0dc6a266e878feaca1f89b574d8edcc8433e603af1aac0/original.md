```
size(hmm, [dim]) -> Int | Tuple
```

Return the number of states in `hmm` and the dimension of the observations.

**Example**

```jldoctest
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
size(hmm)
# output
(2, 1)
```
