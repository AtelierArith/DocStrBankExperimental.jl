```julia
sethopping!(ftm::FTBModel, R::AbstractVector{Int64}, n::Int64, m::Int64,
    p::Int64, hopping::Number)
```

Set ⟨⟨0; n e^{-ilΩt}|H(t)|R; m e^{-i(l-p)Ωt}⟩⟩ to `hopping` for all l. Alternatively, `hopping` is ⟨n|H(p)|m⟩, where H(t) = ∑H(p)e^{-ipΩt}.

The Floquet Hamiltonian H*F=H-i∂t, in the basis functions |n⟩e^{-ilΩt}, is (H*F)*{l, l-p}=⟨⟨0; n e^{-ilΩt}|H(t)|R; m e^{-i(l-p)Ωt}⟩⟩-δ*{p,0}lΩ. This function automatically handles the above δ function.
