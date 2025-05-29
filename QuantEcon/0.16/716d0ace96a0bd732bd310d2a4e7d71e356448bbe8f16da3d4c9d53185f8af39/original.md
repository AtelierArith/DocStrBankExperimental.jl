Type used to evaluate CRRA utility. CRRA utility takes the form

u(c) = ξ c^(1 - γ) / (1 - γ)

Additionally, this code assumes that if c < 1e-10 then

u(c) = ξ (1e-10^(1 - γ) / (1 - γ) + 1e-10^(-γ) * (c - 1e-10))
