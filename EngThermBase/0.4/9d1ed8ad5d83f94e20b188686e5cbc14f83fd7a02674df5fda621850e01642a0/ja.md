`struct T_amt{𝗽<:PREC,𝘅<:EXAC} <: WProperty{𝗽,𝘅}`

Kに基づく精度および正確性のパラメトリック温度量。

`T_amt{𝗽,𝘅}`のパラメータは次のとおりです：

  * 精度 `𝗽<:Union{Float16,Float32,Float64,BigFloat}`;
  * 正確性 `𝘅<:Union{EX,MM}`、すなわち、単一の正確な値または不確実性を伴う測定のいずれかです。

`T_amt`は次の引数タイプからネイティブに構築できます：

  * プレーンで単位のない浮動小数点数;
  * プレーンで単位のない`Measurement`、したがって、任意の`AbstractFloat`;
  * 互換性のある単位を持つ`Quantity{AbstractFloat}`。

コンストラクタは引数からすべてのパラメータを決定します。

## 階層

`T_amt <: WProperty <: WholeAmt <: AMOUNTS <: AbstractTherm <: Any`
