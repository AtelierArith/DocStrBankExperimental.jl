```
DiffREN(ps::AbstractRENParams{T}) where T
```

直接的なパラメータ化から微分可能なRENを構築します。

`DiffREN`は、モデルが呼び出されるたびに明示的なパラメータ化[`ExplicitRENParams`](@ref)を計算する代わりに、`REN`オブジェクトに保存する[`REN`](@ref)や[`WrapREN`](@ref)の代替手段です。

このモデルラッパーは、モデルの呼び出し後にモデルパラメータを更新する予定がある場合に最も使いやすいです。他の[`Flux.jl`](http://fluxml.ai/Flux.jl/stable/)モデルと同様にトレーニングでき（[`WrapREN`](@ref)とは異なり）、トレーニング可能なパラメータが更新されても再作成する必要はありません（[`REN`](@ref)とは異なり）。

ただし、パラメータを更新する前にモデルが何度も呼び出される場合（例：強化学習）には遅く、計算効率が悪くなります。

# 例

`DiffREN`を構築するための構文は、[`REN`](@ref)のものと同じです。

```julia
using RobustNeuralNetworks

nu, nx, nv, ny = 1, 10, 20, 1
ren_params = ContractingRENParams{Float64}(nu, nx, nv, ny)
model = DiffREN(ren_params)
```

[`AbstractREN`](@ref)、[`REN`](@ref)、および[`WrapREN`](@ref)も参照してください。
