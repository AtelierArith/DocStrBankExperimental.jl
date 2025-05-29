Type used to evaluate constant Frisch elasticity (CFE) utility. CFE utility takes the form

v(l) = ξ l^(1 + 1/ϕ) / (1 + 1/ϕ)

Additionally, this code assumes that if l < 1e-10 then

v(l) = ξ (1e-10^(1 + 1/ϕ) / (1 + 1/ϕ) - 1e-10^(1/ϕ) * (1e-10 - l))
