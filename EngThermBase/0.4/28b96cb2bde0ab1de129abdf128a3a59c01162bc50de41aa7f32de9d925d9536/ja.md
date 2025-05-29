`struct ø_amt{𝗽<:PREC,𝘅<:EXAC} <: WUnranked{𝗽,𝘅}`

精度および正確性に基づくパラメトリックな無次元比率量。

`ø_amt{𝗽,𝘅}` のパラメータは次のとおりです：

  * 精度 `𝗽<:Union{Float16,Float32,Float64,BigFloat}`;
  * 正確性 `𝘅<:Union{EX,MM}`、すなわち、単一の正確な値または不確実性を伴う測定のいずれかです。

`ø_amt` は次の引数タイプからネイティブに構築できます：

  * プレーンな単位のない浮動小数点数;
  * プレーンな単位のない `Measurement`、したがって、任意の `AbstractFloat`;
  * 互換性のある単位を持つ `Quantity{AbstractFloat}`。

コンストラクタは引数からすべてのパラメータを決定します。

## 階層

`ø_amt <: WUnranked <: WholeAmt <: AMOUNTS <: AbstractTherm <: Any`
