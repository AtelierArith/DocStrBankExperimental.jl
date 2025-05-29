`v_(x::idealGas{𝕡,𝕩}, P::P_amt{𝕢,𝕪}, T::T_amt{𝕣,𝕫}, B::Type{<:IntBase} = DEF[:IB])::v_amt{𝕡,𝕩,B}`

Returns the specific volume (at base `B`) for the ideal gas `x` at specified pressure `P` and temperature `T`.  Contrary to most `julia` methods, the `x::idealGas{𝕡,𝕩}` model sets the return value precision and exactness, `{𝕡,𝕩}` instead of performing data type promotions. If ommitted, the base `B` defaults to `DEF[:IB]` (from `EngThermBase`).
