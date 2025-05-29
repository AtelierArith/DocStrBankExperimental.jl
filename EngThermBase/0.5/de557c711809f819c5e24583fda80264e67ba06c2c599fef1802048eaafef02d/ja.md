`struct beamt{𝗽<:PREC,𝘅<:EXAC} <: WProperty{𝗽,𝘅}`

体積膨張の精度および正確性のパラメトリック係数は/Kに基づいています。

`beamt{𝗽,𝘅}` パラメータは次のとおりです：

  * 精度 `𝗽<:Union{Float16,Float32,Float64,BigFloat}`;
  * 正確性 `𝘅<:Union{EX,MM}`、すなわち、単一の正確な値または不確実性を伴う測定のいずれかです。

`beamt` は次の引数タイプからネイティブに構築できます：

  * プレーンで単位のない浮動小数点数;
  * プレーンで単位のない `Measurement`、したがって、任意の `AbstractFloat`;
  * 互換性のある単位を持つ `Quantity{AbstractFloat}`。

コンストラクタは引数からすべてのパラメータを決定します。

## 階層

`beamt <: WProperty <: WholeAmt <: AMOUNTS <: AbstractTherm <: Any`
