```
rand([rng, ]hmm, z) -> Array
```

軌道 `z` に従った `hmm` からのサンプル観測。

**出力**

  * `Vector{Float64}` （`Univariate` HMMの場合）：観測値 (`T`)。
  * `Matrix{Float64}` （`Multivariate` HMMの場合）：観測値 (`T x dim(obs)`)。

**例**

```julia
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
y = rand(hmm, [1, 1, 2, 2, 1])
```
