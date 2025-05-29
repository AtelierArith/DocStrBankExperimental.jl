```
DiffLBDN(ps::AbstractLBDNParams)
```

直接パラメータ化から微分可能なLBDNを構築します。

`DiffLBDN`は、モデルが呼び出されるたびに明示的なパラメータ化[`ExplicitLBDNParams`](@ref)を計算する代替手段であり、`LBDN`オブジェクトに保存するのではありません。

このモデルラッパーは、モデルの呼び出し後にモデルパラメータを更新する予定がある場合に最も使いやすいです。他の[`Flux.jl`](http://fluxml.ai/Flux.jl/stable/)モデルと同様にトレーニングでき、トレーニング可能なパラメータが更新されても再作成する必要はありません（[`LBDN`](@ref)とは異なります）。

ただし、パラメータを更新する前にモデルが何度も呼び出される場合（例：強化学習）には遅く、計算効率が悪くなります。

# 例

`DiffLBDN`を構築するための構文は、[`LBDN`](@ref)のものと同じです。

```julia
using RobustNeuralNetworks

nu, nh, ny, γ = 1, [10, 20], 1
lbdn_params = DenseLBDNParams{Float64}(nu, nh, ny, γ)
model = DiffLBDN(lbdn_params)
```

他にも[`AbstractLBDN`](@ref)、[`LBDN`](@ref)、[`SandwichFC`](@ref)を参照してください。
