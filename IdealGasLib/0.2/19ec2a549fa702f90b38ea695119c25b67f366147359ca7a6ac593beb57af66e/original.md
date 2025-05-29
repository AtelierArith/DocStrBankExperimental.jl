`(T_(x::idealGas{𝕡,𝕩}, P::P_amt{𝕢,𝕪}, v::v_amt{𝕣,𝕫})::T_amt{𝕡,𝕩}) where {𝕡,𝕢,𝕣,𝕩,𝕪,𝕫}`

Returns the temperature for the ideal gas `x` at specified pressure `P` and specific volume `v`. Contrary to most `julia` methods, the `x::idealGas{𝕡,𝕩}` model sets the return value precision and exactness, `{𝕡,𝕩}` instead of performing data type promotions.
