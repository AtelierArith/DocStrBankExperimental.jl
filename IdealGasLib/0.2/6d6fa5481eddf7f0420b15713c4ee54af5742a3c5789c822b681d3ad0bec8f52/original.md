`(u_(𝐻::nobleGasHeat{𝕡,𝕩},      𝑇::T_amt{𝕢,𝕪},      B::Type{<:IntBase}=DEF[:IB])::u_amt{𝕡,𝕩,B}) where {𝕡,𝕢,𝕩,𝕪}`

Returns the particular gas specific internal energy in the specified or default base for the substance with specific heat modeled by `𝐻`, for states with temperature `𝑇`. Resulting precision, PREC, and exactness, EXAC, are model-driven, and not promotion-driven.
