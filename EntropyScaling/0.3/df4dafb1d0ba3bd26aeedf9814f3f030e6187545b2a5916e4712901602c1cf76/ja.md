```
ChapmanEnskogModel <: AbstractTransportPropertyModel
```

ゼロ密度限界のためのチャップマン-エンスコグ輸送特性。

# フィールド

  * `σ::Vector{T}`: レナード-ジョーンズサイズパラメータ (`[σ] = m`)
  * `ε::Vector{T}`: レナード-ジョーンズエネルギーパラメータ (`[ε] = J`)
  * `Mw::Vector{T}`: モル質量 (`[Mw] = kg mol⁻¹`)
  * `collision::C`: 衝突積分法 (`KimMonroe()` (デフォルト) または `Neufeld()`、詳細は [`Ω`](@ref) を参照)

# コンストラクタ

  * `ChapmanEnskogModel(components; collision_integral=KimMonroe(), ref="", ref_id="")`: データベースコンストラクタ
  * `ChapmanEnskogModel(components, σ, ε, Mw; collision_integral=KimMonroe())`: カスタムパラメータコンストラクタ

入力引数は単一の値（純粋）またはベクトルのいずれかであることができます。キーワード `ref`（短い参照）および `ref_id`（DOIまたはISBN）を使用して参照を指定できます。現在、[poling*properties*2001](@citet) および [yang*linking*2022](@citet) からのパラメータがデータベースに含まれています。混合物の特性は、[wilke*viscosity*1950](@citet)（粘度）、[mason*approximate*1958](@citet)（熱伝導率）、および [miller*self-diffusion*1961](@citet)（自己拡散）からのモデルに従って計算されます。

# 例

```julia
using EntropyScaling 

# カスタムパラメータでの構築
σ, ε, Mw = 3.758e-10, 148.6*EntropyScaling.kB, 16.043e-3            # Poling et al. から
model_methane = ChapmanEnskogModel("methane",σ,ε,Mw)

η_mix = viscosity(model_methane, NaN, 300.)
D_mix = self_diffusion_coefficient(model_methane, NaN, 300.)

# データベースからの構築
model_mix = ChapmanEnskogModel(["butane","methanol"]; ref="Poling et al. (2001)")

η_mix = viscosity(model_mix, NaN, 300., [.5,.5])
D_mix = self_diffusion_coefficient(model_mix, NaN, 300., [.5,.5])  
```
