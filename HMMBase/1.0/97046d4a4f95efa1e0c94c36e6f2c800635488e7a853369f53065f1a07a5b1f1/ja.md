```
rand([rng, ]hmm, T; init, seq) -> Array | (Vector, Array)
```

`hmm`から`T`タイムステップの軌跡をサンプリングします。

**キーワード引数**

  * `init::Integer = rand(Categorical(hmm.a))`: 初期状態。
  * `seq::Bool = false`: 隠れ状態のシーケンスを返すかどうか。

**出力**

  * `Vector{Int}` (もし`seq == true`の場合): 隠れ状態のシーケンス。
  * `Vector{Float64}` (単変量HMMの場合): 観測値 (`T`)。
  * `Matrix{Float64}` (多変量HMMの場合): 観測値 (`T x dim(obs)`)。

**例**

```julia
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
y = rand(hmm, 1000) # または
z, y = rand(hmm, 1000, seq = true)
size(y) # (1000,)
```

```julia
using Distributions, HMMBase
hmm = HMM([0.9 0.1; 0.1 0.9], [MvNormal(ones(2)), MvNormal(ones(2))])
y = rand(hmm, 1000) # または
z, y = rand(hmm, 1000, seq = true)
size(y) # (1000, 2)
```
