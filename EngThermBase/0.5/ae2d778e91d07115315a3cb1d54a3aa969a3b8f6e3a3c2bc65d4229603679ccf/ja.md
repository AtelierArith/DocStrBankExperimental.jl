`struct Maamt{𝗽<:PREC,𝘅<:EXAC} <: WProperty{𝗽,𝘅}`

精度および正確性に基づくパラメトリックマッハ数の量。

`Maamt{𝗽,𝘅}` パラメータは次のとおりです：

  * 精度 `𝗽<:Union{Float16,Float32,Float64,BigFloat}`;
  * 正確性 `𝘅<:Union{EX,MM}`、すなわち、単一の正確な値または不確実性を伴う測定のいずれかです。

`Maamt` は次の引数タイプからネイティブに構築できます：

  * 単純な無次元浮動小数点数;
  * 単純な無次元 `Measurement`、したがって、任意の `AbstractFloat`;
  * 互換性のある単位を持つ `Quantity{AbstractFloat}`。

コンストラクタは引数からすべてのパラメータを決定します。

## 階層

`Maamt <: WProperty <: WholeAmt <: AMOUNTS <: AbstractTherm <: Any`
