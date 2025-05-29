`(Δu(𝐻::nobleGasHeat{𝕡,𝕩},      𝒾::T_amt{𝕢,𝕪},      𝒻::T_amt{𝕣,𝕫},      B::Type{<:IntBase} = DEF[:IB])::deamt{𝕡,𝕩,B}) where {𝕡,𝕢,𝕣,𝕩,𝕪,𝕫}`

Returns the particular gas variation in specific internal energy in the specified or default base for the substance with specific heat modeled by `𝐻`, for process with initial and final temperatures of `i` and `f`, respectively. Resulting precision, PREC, and exactness, EXAC, are model-driven, and not promotion-driven.
