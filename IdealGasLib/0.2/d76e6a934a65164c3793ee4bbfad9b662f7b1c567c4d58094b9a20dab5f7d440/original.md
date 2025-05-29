`(ds(𝐻::nobleGasHeat{𝕡,𝕩},      Ti::T_amt{𝕢,𝕪},      Tf::T_amt{𝕣,𝕫},      Pi::P_amt{𝕟,𝕧},      Pf::P_amt{𝕠,𝕨},      B::Type{<:IntBase} = DEF[:IB])::dsamt{𝕡,𝕩,B}) where {𝕟,𝕠,𝕡,𝕢,𝕣,𝕧,𝕨,𝕩,𝕪,𝕫}`

Returns the particular gas variation in specific entropy in the specified or default base for the substance with specific heat modeled by `𝐻`, for process with initial and final temperatures and pressures of `Ti` and `Tf`, and `Pi` and `Pf`, respectively. Resulting precision, PREC, and exactness, EXAC, are model-driven, and not promotion-driven.
