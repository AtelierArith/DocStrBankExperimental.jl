`struct s_amt{𝗽<:PREC,𝘅<:EXAC,𝗯<:BASE} <: BProperty{𝗽,𝘅,𝗯}`

kJ/Kに基づく精度、正確性、基準のパラメトリックエントロピー量。

`s_amt{𝗽,𝘅,𝗯}` パラメータは次のとおりです：

  * 精度 `𝗽<:Union{Float16,Float32,Float64,BigFloat}`;
  * 正確性 `𝘅<:Union{EX,MM}`、すなわち、単一の正確な値または不確実性を伴う測定のいずれか;
  * 熱力学的基準 `𝗯<:Union{SY,DT,MA,MO}` は、それぞれシステム、レート、質量、またはモル量に対して、kJ K^-1、kJ K^-1 s^-1、kJ kg^-1 K^-1、または kJ K^-1 kmol^-1 の単位で表されます。

`s_amt` は次の引数タイプからネイティブに構築できます：

  * プレーンで単位のない浮動小数点数;
  * プレーンで単位のない `Measurement`；したがって、任意の `AbstractFloat`;
  * 互換性のある単位を持つ `Quantity{AbstractFloat}`。

コンストラクタは引数からパラメータを決定します。`Quantity` コンストラクタは基準引数を必要としません。プレーンな `AbstractFloat` のものは基準引数を必要とします。

## 階層

`s_amt <: BProperty <: BasedAmt <: AMOUNTS <: AbstractTherm <: Any`
