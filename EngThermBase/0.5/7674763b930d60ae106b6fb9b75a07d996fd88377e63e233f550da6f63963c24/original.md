`struct __amt{𝗽<:PREC,𝘅<:EXAC} <: GenerAmt{𝗽,𝘅}`

Precision-, and Exactness- parametric generic amounts based in arbitrary units.

`__amt{𝗽,𝘅}` parameters are:

  * Precision `𝗽<:Union{Float16,Float32,Float64,BigFloat}`;
  * Exactness `𝘅<:Union{EX,MM}`, i.e., either a single, precise value or an uncertainty-bearing measurement, respectively;

A `__amt` can be natively constructed from the following argument types:

  * A plain, unitless float;
  * A plain, unitless `Measurement`; hence, any `AbstractFloat`;
  * A `Quantity{AbstractFloat}` with any units.

## Hierarchy

`__amt <: GenerAmt <: AMOUNTS <: AbstractTherm <: Any`
