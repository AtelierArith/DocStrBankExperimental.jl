```
RefpropRESModel{T} <: AbstractEntropyScalingModel
```

Refprop EOSに基づくエントロピースケーリングモデル [yang*linking*2022,yang*entropy*2021](@cite)。 

データベースは、いくつかの流体の粘度に対してすぐに使用できるモデルを提供します。このモデルは、[`Clapeyron.jl`](https://github.com/ClapeyronThermo/Clapeyron.jl) および [`Coolprop.jl`](https://github.com/CoolProp/CoolProp.jl) と組み合わせて使用するのに適しています（例を参照）。

# パラメータ

  * `n::Matrix{T}`: 成分特有の *または* グローバル（グループ）パラメータ
  * `ξ::Vector{T}`: グローバルパラメータが使用される場合の成分特有のスケーリングパラメータ（`ξ = 1` は個別フィット用）
  * `σ::Vector{T}`: チャップマン-エンスコグモデルのLJサイズパラメータ
  * `ε::Vector{T}`: チャップマン-エンスコグモデルのLJエネルギーパラメータ
  * `crit::Dict{Symbol,Vector}`: 熱伝導率の臨界寄与のためのパラメータ（キー: `:φ0`, `:Γ`, `:qD`, および `:Tref`）

# コンストラクタ

  * `RefpropRESModel(eos, params::Dict{P})`: デフォルトコンストラクタ（上記参照）。
  * `RefpropRESModel(eos, components)`: データベースに提供されたパラメータを使用してESモデルを作成します（推奨）。 `RefpropRESModel(components)` は、EOSモデルをオンザフライで作成します（`Clapeyron.jl` と `Coolprop.jl` がロードされている場合のみ機能します）。

!!! info
    ここではデフォルトのCoolProp EOSが使用されており、必ずしも元の論文の選択と一致するわけではありません。 これにより、元の論文の値に対してわずかな偏差が生じる可能性があります（特に熱伝導率について）。


# 例

```julia
using EntropyScaling, Clapeyron, CoolProp

model_pure = RefpropRESModel("R134a")
η_pure = viscosity(model_pure, 1e5, 300.; phase=:liquid)

model_mix = RefpropRESModel(["decane","butane"])
η_mix = viscosity(model_mix, 1e5, 300., [.5,.5])
```
