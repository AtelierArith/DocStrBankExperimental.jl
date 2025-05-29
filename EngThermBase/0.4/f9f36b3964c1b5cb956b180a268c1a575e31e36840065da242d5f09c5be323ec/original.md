`struct s_amt{𝗽<:PREC,𝘅<:EXAC,𝗯<:BASE} <: BProperty{𝗽,𝘅,𝗯}`

Precision-, Exactness-, and Base- parametric entropy amounts based in kJ/K.

`s_amt{𝗽,𝘅,𝗯}` parameters are:

  * Precision `𝗽<:Union{Float16,Float32,Float64,BigFloat}`;
  * Exactness `𝘅<:Union{EX,MM}`, i.e., either a single, precise value or an uncertainty-bearing measurement, respectively;
  * Thermodynamic base `𝗯<:Union{SY,DT,MA,MO}` respectively for system, rate, mass, or molar quantities, respectively in units of kJ K^-1, kJ K^-1 s^-1, kJ kg^-1 K^-1, or kJ K^-1 kmol^-1.

A `s_amt` can be natively constructed from the following argument types:

  * A plain, unitless float;
  * A plain, unitless `Measurement`; hence, any `AbstractFloat`;
  * A `Quantity{AbstractFloat}` with compatible units.

Constructors determine parameters from their arguments. `Quantity` constructors do not need a base argument. Plain, `AbstractFloat` ones require the base argument.

## Hierarchy

`s_amt <: BProperty <: BasedAmt <: AMOUNTS <: AbstractTherm <: Any`
