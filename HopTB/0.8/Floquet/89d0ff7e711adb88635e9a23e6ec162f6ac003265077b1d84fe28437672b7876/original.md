```julia
addhopping!(ftm::FTBModel, R::AbstractVector{Int64}, n::Int64, m::Int64,
    p::Int64, hopping::Number)
```

Add `hopping` to ⟨⟨0; n e^{-ilΩt}|H(t)|R; m e^{-i(l-p)Ωt}⟩⟩.

This function does not add the onsite energy due to periodic driving.
