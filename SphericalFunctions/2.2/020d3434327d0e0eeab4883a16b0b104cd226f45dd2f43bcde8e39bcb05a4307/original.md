WignerHindex(ℓ, m′, m, m′ₘₐₓ)

Helper function for [`WignerHindex`](@ref), with more constraints.

This function assumes that `m ≥ |m′|`.  The main [`WignerHindex`](@ref) function uses symmetries of the H array to account for cases that violate this assumption.  (But note that both that function and this one assume that `|m| ≤ ℓ` and `|m′| ≤ ℓ`.)
