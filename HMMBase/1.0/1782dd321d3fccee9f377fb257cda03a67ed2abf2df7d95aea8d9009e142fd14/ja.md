```
forward(hmm, observations; robust) -> (Vector, Float)
```

`hmm`モデルに与えられた`observations`の前向き確率を計算します。

**出力**

  * `Vector{Float64}`: 前向き確率。
  * `Float64`: 観測された系列の対数尤度。

**例**

```julia
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
y = rand(hmm, 1000)
probs, tot = forward(hmm, y)
```
