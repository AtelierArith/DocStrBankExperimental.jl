`struct ø_amt{𝗽<:PREC,𝘅<:EXAC} <: WUnranked{𝗽,𝘅}`

Precision-, and Exactness- parametric generic dimensionless ratio amounts based in –.

`ø_amt{𝗽,𝘅}` parameters are:

  * Precision `𝗽<:Union{Float16,Float32,Float64,BigFloat}`;
  * Exactness `𝘅<:Union{EX,MM}`, i.e., either a single, precise value or an uncertainty-bearing measurement, respectively;

A `ø_amt` can be natively constructed from the following argument types:

  * A plain, unitless float;
  * A plain, unitless `Measurement`; hence, any `AbstractFloat`;
  * A `Quantity{AbstractFloat}` with compatible units.

Constructors determine all parameters from their arguments.

## Hierarchy

`ø_amt <: WUnranked <: WholeAmt <: AMOUNTS <: AbstractTherm <: Any`
