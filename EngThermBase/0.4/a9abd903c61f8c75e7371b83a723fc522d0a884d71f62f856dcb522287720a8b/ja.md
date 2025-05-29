`struct gvamt{𝗽<:PREC,𝘅<:EXAC} <: WUnranked{𝗽,𝘅}`

精度と正確性に基づく重力量（m/s²）。

`gvamt{𝗽,𝘅}` のパラメータは次のとおりです：

  * 精度 `𝗽<:Union{Float16,Float32,Float64,BigFloat}`;
  * 正確性 `𝘅<:Union{EX,MM}`、すなわち、単一の正確な値または不確実性を伴う測定のいずれかです。

`gvamt` は次の引数タイプからネイティブに構築できます：

  * 単純な無次元の浮動小数点数；
  * 単純な無次元の `Measurement`；したがって、任意の `AbstractFloat`；
  * 互換性のある単位を持つ `Quantity{AbstractFloat}`。

コンストラクタは引数からすべてのパラメータを決定します。

## 階層

`gvamt <: WUnranked <: WholeAmt <: AMOUNTS <: AbstractTherm <: Any`
