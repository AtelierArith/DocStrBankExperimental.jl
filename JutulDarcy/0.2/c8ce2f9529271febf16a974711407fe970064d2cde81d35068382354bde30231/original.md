```
component_mass_fluxes!(q, face, state, model::StandardBlackOilModel, flux_type, kgrad, upw)
```

Compute the component mass fluxes for a given face in a black oil model.

# Arguments

  * `q`: Output array to store the computed mass fluxes.
  * `face`: The face for which the fluxes are being computed.
  * `state`: The current state of the system.
  * `model::StandardBlackOilModel`: The black oil model being used.
  * `flux_type`: The type of flux calculation to be performed.
  * `kgrad`: Gradient operator for K grad p.
  * `upw`: Upwind scheme to be used for the flux calculation.

# Returns

  * This function modifies the `q` array in place with the computed mass fluxes.
