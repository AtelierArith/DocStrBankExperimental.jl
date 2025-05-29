`struct e_amt{𝗽<:PREC,𝘅<:EXAC,𝗯<:BASE} <: BProperty{𝗽,𝘅,𝗯}`

kJに基づく精度、正確さ、基準のパラメトリックな総エネルギー量。

`e_amt{𝗽,𝘅,𝗯}`のパラメータは次のとおりです：

  * 精度 `𝗽<:Union{Float16,Float32,Float64,BigFloat}`;
  * 正確さ `𝘅<:Union{EX,MM}`、すなわち、単一の正確な値または不確実性を伴う測定のいずれか;
  * 熱力学的基準 `𝗯<:Union{SY,DT,MA,MO}` はそれぞれ、システム、レート、質量、またはモル量に対して、kJ、kJ s^-1、kJ kg^-1、またはkJ kmol^-1の単位で表されます。

`e_amt`は次の引数タイプからネイティブに構築できます：

  * プレーンで単位のない浮動小数点数;
  * プレーンで単位のない`Measurement`、したがって、任意の`AbstractFloat`;
  * 互換性のある単位を持つ`Quantity{AbstractFloat}`。

コンストラクタは引数からパラメータを決定します。`Quantity`コンストラクタは基準引数を必要としません。プレーンな`AbstractFloat`のものは基準引数を必要とします。

## 階層

`e_amt <: BProperty <: BasedAmt <: AMOUNTS <: AbstractTherm <: Any`
