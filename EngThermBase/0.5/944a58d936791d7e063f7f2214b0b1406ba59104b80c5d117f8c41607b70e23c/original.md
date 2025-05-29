`struct xiamt{𝗽<:PREC,𝘅<:EXAC,𝗯<:BASE} <: BProperty{𝗽,𝘅,𝗯}`

Precision-, Exactness-, and Base- parametric closed sys. exergy amounts based in kJ.

`xiamt{𝗽,𝘅,𝗯}` parameters are:

  * Precision `𝗽<:Union{Float16,Float32,Float64,BigFloat}`;
  * Exactness `𝘅<:Union{EX,MM}`, i.e., either a single, precise value or an uncertainty-bearing measurement, respectively;
  * Thermodynamic base `𝗯<:Union{SY,DT,MA,MO}` respectively for system, rate, mass, or molar quantities, respectively in units of kJ, kJ s^-1, kJ kg^-1, or kJ kmol^-1.

A `xiamt` can be natively constructed from the following argument types:

  * A plain, unitless float;
  * A plain, unitless `Measurement`; hence, any `AbstractFloat`;
  * A `Quantity{AbstractFloat}` with compatible units.

Constructors determine parameters from their arguments. `Quantity` constructors do not need a base argument. Plain, `AbstractFloat` ones require the base argument.

## Hierarchy

`xiamt <: BProperty <: BasedAmt <: AMOUNTS <: AbstractTherm <: Any`
