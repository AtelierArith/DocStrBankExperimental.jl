```
random_markov_chain([rng], n[, k])
```

`n` 状態を持つランダムにサンプリングされた MarkovChain インスタンスを返します。各状態は正の遷移確率を持つ `k` 状態を持ちます。

# 引数

  * `rng::AbstractRNG=GLOBAL_RNG` : 擬似乱数生成器。
  * `n::Integer` : 状態の数。
  * `k::Integer=n` : 行列の各列の非ゼロエントリの数。指定がない場合は `n` に設定されます。

# 戻り値

  * `mc::MarkovChain` : MarkovChain インスタンス。

# 例

```julia
julia> using QuantEcon, Random

julia> rng = MersenneTwister(1234);

julia> mc = random_markov_chain(rng, 3);

julia> mc.p
3×3 LinearAlgebra.Transpose{Float64,Array{Float64,2}}:
 0.590845  0.175952   0.233203
 0.460085  0.106152   0.433763
 0.794026  0.0601209  0.145853

julia> mc = random_markov_chain(rng, 3, 2);

julia> mc.p
3×3 LinearAlgebra.Transpose{Float64,Array{Float64,2}}:
 0.0       0.200586  0.799414
 0.701386  0.0       0.298614
 0.753163  0.246837  0.0
```
