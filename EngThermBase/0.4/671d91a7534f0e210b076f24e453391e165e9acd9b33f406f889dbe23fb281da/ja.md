`struct vramt{𝗽<:PREC,𝘅<:EXAC} <: WProperty{𝗽,𝘅}`

精度および正確性に基づく相対的な特定体積の量。

`vramt{𝗽,𝘅}` パラメータは次のとおりです：

  * 精度 `𝗽<:Union{Float16,Float32,Float64,BigFloat}`;
  * 正確性 `𝘅<:Union{EX,MM}`、すなわち、単一の正確な値または不確実性を伴う測定のいずれか。

`vramt` は次の引数タイプからネイティブに構築できます：

  * プレーンな無次元浮動小数点数;
  * プレーンな無次元 `Measurement`、したがって、任意の `AbstractFloat`;
  * 互換性のある単位を持つ `Quantity{AbstractFloat}`。

コンストラクタは引数からすべてのパラメータを決定します。

## 階層

`vramt <: WProperty <: WholeAmt <: AMOUNTS <: AbstractTherm <: Any`
