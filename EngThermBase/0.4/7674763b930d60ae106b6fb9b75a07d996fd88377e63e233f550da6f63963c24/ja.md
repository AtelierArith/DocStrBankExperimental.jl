`struct __amt{𝗽<:PREC,𝘅<:EXAC} <: GenerAmt{𝗽,𝘅}`

任意の単位に基づく精度および正確性のパラメトリックジェネリック量。

`__amt{𝗽,𝘅}` パラメータは次のとおりです：

  * 精度 `𝗽<:Union{Float16,Float32,Float64,BigFloat}`；
  * 正確性 `𝘅<:Union{EX,MM}`、すなわち、単一の正確な値または不確実性を伴う測定のいずれか；

`__amt` は次の引数タイプからネイティブに構築できます：

  * プレーンな単位なしの浮動小数点数；
  * プレーンな単位なしの `Measurement`；したがって、任意の `AbstractFloat`；
  * 任意の単位を持つ `Quantity{AbstractFloat}`。

## 階層

`__amt <: GenerAmt <: AMOUNTS <: AbstractTherm <: Any`
