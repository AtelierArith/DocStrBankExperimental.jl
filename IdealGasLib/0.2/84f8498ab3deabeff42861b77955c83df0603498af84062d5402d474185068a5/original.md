`(P_(x::idealGas{𝕡,𝕩}, T::T_amt{𝕢,𝕪}, v::v_amt{𝕣,𝕫})::P_amt{𝕡,𝕩}) where {𝕡,𝕢,𝕣,𝕩,𝕪,𝕫}`

Returns the pressure for the ideal gas `x` at specified temperature `T` and specific volume `v`. Contrary to most `julia` methods, the `x::idealGas{𝕡,𝕩}` model sets the return value precision and exactness, `{𝕡,𝕩}` instead of performing data type promotions.
