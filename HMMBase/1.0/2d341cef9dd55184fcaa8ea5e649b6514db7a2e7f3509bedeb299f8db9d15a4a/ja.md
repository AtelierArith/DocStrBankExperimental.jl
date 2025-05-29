```
loglikelihoods(hmm, observations; robust) -> Matrix
```

状態ごとおよび観測ごとの対数尤度を返します。

**出力**

  * `Matrix{Float64}`: 対数尤度行列 (`T x K`)。

**例**

```julia
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
y = rand(hmm, 1000)
LL = likelihoods(hmm, y)
```
