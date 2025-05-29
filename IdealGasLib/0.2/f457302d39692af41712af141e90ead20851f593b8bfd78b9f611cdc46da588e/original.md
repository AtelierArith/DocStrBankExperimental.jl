`(ds(𝐻::nobleGasHeat{𝕡,𝕩},     Ti::T_amt{𝕢,𝕪},     Tf::T_amt{𝕣,𝕫},     vi::v_amt{𝕟,𝕧,𝕓},     vf::v_amt{𝕠,𝕨,𝕓},     B::Type{<:IntBase} = DEF[:IB])::dsamt{𝕡,𝕩,B}) where {𝕓,𝕟,𝕠,𝕡,𝕢,𝕣,𝕧,𝕨,𝕩,𝕪,𝕫}`

Returns the particular gas variation in specific entropy in the specified or default base for the substance with specific heat modeled by `𝐻`, for process with initial and final temperatures and specific volumes of `Ti` and `Tf`, and `vi` and `vf`, respectively. Resulting precision, PREC, and exactness, EXAC, are model-driven, and not promotion-driven.
