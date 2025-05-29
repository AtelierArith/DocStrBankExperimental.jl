```
posteriors(hmm, observations; robust) -> Vector
```

サンプルの尤度を使用して事後確率を計算します。

**例**

```julia
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
y = rand(hmm, 1000)
γ = posteriors(hmm, y)
```
