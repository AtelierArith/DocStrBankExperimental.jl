```
derivative_estimate(X, p, alg::AbstractStochasticADAlgorithm = ForwardAlgorithm(PrunedFIsBackend()); direction=nothing, alg_data::NamedTuple = (;))
```

無偏推定量 $\frac{\mathrm{d}\mathbb{E}[X(p)]}{\mathrm{d}p}$ を計算します。これは、ランダム関数 `X(p)` の期待値の入力 `p` に関する導関数です。

`p` と `X(p)` は、[`Functors.jl`](https://fluxml.ai/Functors.jl/stable/) によってサポートされる任意のオブジェクト（スカラーや抽象配列など）であることができます。`derivative_estimate` の出力は `p` と同じ外部構造を持ちますが、`p` の各スカラーは、そのエントリに関する `X(p)` の導関数推定に置き換えられます。たとえば、`X(p) <: AbstractMatrix` かつ `p <: Real` の場合、出力は行列になります。

`alg` キーワード引数は、導関数推定を計算するために使用される [アルゴリズム](public_api.md#Algorithms) を指定します。後方互換性のために、追加のシグネチャ `derivative_estimate(X, p; backend, direction=nothing)` もサポートされており、これはデフォルトで提供された `backend` を使用して `ForwardAlgorithm` を使用します。`alg_data` キーワード引数は、特定のアルゴリズムが受け入れるまたは必要とする追加のデータを指定できます。

`direction` が提供されると、出力はその方向での `p` の摂動に関してのみ微分されます。

# 例

```jldoctest
julia> using Distributions, Random, StochasticAD; Random.seed!(4321);

julia> derivative_estimate(rand ∘ Bernoulli, 0.5) # 真の導関数に平均化されるランダム量。
2.0

julia> derivative_estimate(x -> [rand(Bernoulli(x * i/4)) for i in 1:3], 0.5)
3-element Vector{Float64}:
 0.2857142857142857
 0.6666666666666666
 0.0
```
