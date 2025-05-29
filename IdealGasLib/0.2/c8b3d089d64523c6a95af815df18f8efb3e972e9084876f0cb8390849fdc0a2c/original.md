`(rebase(𝐻::nobleGasHeat{𝕡,𝕩}, 𝑇::T_amt{𝕡,𝕩}, 𝑃::P_amt{𝕡,𝕩})::nobleGasHeat{𝕡,𝕩}) where {𝕡,𝕩}`

Returns a `nobleGasHeat` instance based on `𝐻` with `(Tref, Pref) = (𝑇, 𝑃)`, and with `sref` adjusted so as to yield same entropy values for the same `(T, P)` states than `𝐻`. Values of `s°` will also coincide only if `𝐻.Pref == 𝑃`.
