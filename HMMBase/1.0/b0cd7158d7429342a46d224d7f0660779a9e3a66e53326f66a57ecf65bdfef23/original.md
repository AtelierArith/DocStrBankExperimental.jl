```
permute(hmm, perm) -> HMM
```

Permute the states of `hmm` according to `perm`.

**Arguments**

  * `perm::Vector{<:Integer}`: permutation of the states.

**Example**

```julia
using Distributions, HMMBase
hmm = HMM([0.8 0.2; 0.1 0.9], [Normal(0,1), Normal(10,1)])
hmm = permute(hmm, [2, 1])
hmm.A # [0.9 0.1; 0.2 0.8]
hmm.B # [Normal(10,1), Normal(0,1)]
```
