`(s_(𝐻::nobleGasHeat{𝕡,𝕩},      𝑇::T_amt{𝕢,𝕪},      𝑃::P_amt{𝕣,𝕫},      B::Type{<:IntBase}=DEF[:IB])::s_amt{𝕡,𝕩,B})`

Returns the particular gas specific entropy in the specified or default base for the substance with specific heat modeled by `𝐻`, in the specified thermodynamic state (`𝑇`, `𝑃`). Resulting precision, PREC, and exactness, EXAC, are model-driven, and not promotion-driven.
