`struct mJamt{𝗽<:PREC,𝘅<:EXAC} <: WProperty{𝗽,𝘅}`

精度および正確性に基づくジュール・トムソン係数のパラメトリック量で、K/kPa単位です。

`mJamt{𝗽,𝘅}` のパラメータは次のとおりです：

  * 精度 `𝗽<:Union{Float16,Float32,Float64,BigFloat}`;
  * 正確性 `𝘅<:Union{EX,MM}`、すなわち、単一の正確な値または不確実性を伴う測定のいずれかです。

`mJamt` は次の引数タイプからネイティブに構築できます：

  * プレーンな単位なしの浮動小数点数;
  * プレーンな単位なしの `Measurement`、したがって、任意の `AbstractFloat`;
  * 互換性のある単位を持つ `Quantity{AbstractFloat}`。

コンストラクタは引数からすべてのパラメータを決定します。

## 階層

`mJamt <: WProperty <: WholeAmt <: AMOUNTS <: AbstractTherm <: Any`
