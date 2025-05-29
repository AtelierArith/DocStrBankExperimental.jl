`struct Z_amt{𝗽<:PREC,𝘅<:EXAC} <: WProperty{𝗽,𝘅}`

精度および正確性に基づく一般化された圧縮係数の量 `Z_amt{𝗽,𝘅}` のパラメータは次のとおりです：

  * 精度 `𝗽<:Union{Float16,Float32,Float64,BigFloat}`;
  * 正確性 `𝘅<:Union{EX,MM}`、すなわち、単一の正確な値または不確実性を伴う測定のいずれかです。

`Z_amt` は次の引数タイプからネイティブに構築できます：

  * 単純な無次元の浮動小数点数;
  * 単純な無次元の `Measurement`、したがって、任意の `AbstractFloat`;
  * 互換性のある単位を持つ `Quantity{AbstractFloat}`。

コンストラクタは引数からすべてのパラメータを決定します。

## 階層

`Z_amt <: WProperty <: WholeAmt <: AMOUNTS <: AbstractTherm <: Any`
