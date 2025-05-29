```
nparams(hmm) -> Int
```

Return the number of *free* parameters in `hmm`, without counting the observation distributions parameters.

**Example**

```jldoctest
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
nparams(hmm)
# output
3
```
