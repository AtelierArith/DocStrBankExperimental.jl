```
FrameworkModel{T} <: AbstractEntropyScalingModel
```

エントロピースケーリングフレームワーク [schmitt*entropy*2024,schmitt*entropy*2025](@cite)。

エントロピースケーリングフレームワークは、分子ベースのEOSに基づいて輸送特性（粘度、熱伝導率、拡散係数）をモデル化する物理的な方法を提供します。これにより、少数の実験データのみを使用して新しいモデルをフィッティングすることが可能になります。

# パラメータ

  * `α::Matrix{T}`: 成分特有のパラメータ（サイズ: `5 x N_components`）

`m`（分子ベースのEOSのセグメントパラメータ）および `Y₀⁺min`（スケーリングされたゼロ密度輸送特性の最小値）は、追加の内部パラメータです（構築時に設定しないでください）。

# コンストラクタ

  * `FrameworkModel(eos, params::Dict{P})`: デフォルトコンストラクタ（上記参照）。
  * `FrameworkModel(eos, datasets::Vector{TransportPropertyData}; opts::FitOptions=FitOptions(), solute=nothing)`: 実験データに新しいパラメータ `α` をフィッティングするためのコンストラクタ（純成分にのみ適用可能）。 `datasets` には実験データが含まれています。 [`TransportPropertyData`](@ref)を参照してください。 `opts` は、[`FitOptions`](@ref)を通じてフィッティング手順を制御することを可能にします。 `solute` は溶質のEOSモデル（オプション、無限希釈での拡散係数のフィッティング用）。

# 例

```julia
using EntropyScaling, Clapeyron

# n-ブタンの実験サンプルデータをロード
(T_exp,ϱ_exp,η_exp) = EntropyScaling.load_sample_data()
data = ViscosityData(T_exp, [], ϱ_exp, η_exp, :unknown)

# EOSモデルを作成
eos_model = PCSAFT("butane")

# エントロピースケーリングモデルを作成（パラメータのフィッティング）
model = FrameworkModel(eos_model, [data])

# 状態での粘度の計算
η = viscosity(model, 0.1e6, 300.)
```
