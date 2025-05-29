```
permute(hmm, perm) -> HMM
```

`hmm`の状態を`perm`に従って置換します。

**引数**

  * `perm::Vector{<:Integer}`: 状態の置換。

**例**

```julia
using Distributions, HMMBase
hmm = HMM([0.8 0.2; 0.1 0.9], [Normal(0,1), Normal(10,1)])
hmm = permute(hmm, [2, 1])
hmm.A # [0.9 0.1; 0.2 0.8]
hmm.B # [Normal(10,1), Normal(0,1)]
```
