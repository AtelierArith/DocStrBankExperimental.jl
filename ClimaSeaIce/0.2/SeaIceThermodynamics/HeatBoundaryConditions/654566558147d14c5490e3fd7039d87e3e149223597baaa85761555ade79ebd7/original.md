```
MeltingConstrainedFluxBalance(top_surface_temperature_solver=NonlinearSurfaceTemperatureSolver())
```

Return a boundary condition that determines the top (or "upper surface") temperature $Tᵤ$ to equilibrate the top heat fluxes,

$$
Qₓ₁(Tᵤ) + Qₓ₂(Tᵤ) + ⋯ - Qᵢ = Σᴺ Qₓₙ(Tᵤ) - Qᵢ = δQ ,
$$

where $Qᵢ$ is the intrinsic flux into the top from within the ice (typically, a conductive flux), $Qₓₙ$ represent external fluxes into the air above the ice, $δQ$ is the residual flux, and $Tᵤ$ is the (upper) top temperature. $Tᵤ$ is evaluated under the constraint that

$$
Tᵤ ≤ Tₘ(S),
$$

where $Tₘ(S)$ is the melting temperature, which is a function of the ice salinity at the top, $S$. When $Tᵤ < Tₘ(S)$, the top is frozen and $δQ = 0$. When the constraint operates, such that $Tᵤ = Tₘ(S)$, the top is melting and the residual flux is non-zero.

$$
δQ ≡ Σᴺ Qₙ(Tₘ) - Qᵢ(Tₘ).
$$

The residual flux is consumed by the cost of transforming ice into liquid water, and is related to the rate of change of ice thickness, $h$, by

$$
\frac{dhₛ}{dt} = δQ / ℒ(Tᵤ)
$$

where $ℒ(Tᵤ)$ is the latent heat, equal to the different between the higher internal energy of liquid water and the lower internal energy of solid ice, at the temperature $Tᵤ$.
