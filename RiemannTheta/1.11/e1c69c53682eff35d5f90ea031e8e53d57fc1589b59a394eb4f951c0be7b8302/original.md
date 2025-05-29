```
 riemanntheta(zs::Vector{Vector{ComplexF64}},
```

                  Ω::Matrix{ComplexF64};                   eps::Float64=1e-8,                   derivs::Vector{Vector{ComplexF64}}=Vector{ComplexF64}[],                   accuracy_radius::Float64=5.)::Vector{ComplexF64}

Return the value of the Riemann theta function for Ω and all z in `zs` if `derivs` is empty, or the derivatives at all z in `zs` for the given directional derivatives in `derivs`.

## Parameters

  * `zs` : A vector of complex vectors at which to evaluate the Riemann theta function.
  * `Omega` : A Riemann matrix.
  * `eps` : (Default: 1e-8) The desired numerical accuracy.
  * `derivs` : A vector of complex vectors giving a directional derivative.
  * `accuracy_radius` : (Default: 5.) The radius from the g-dimensional origin

where the requested accuracy of the Riemann theta is guaranteed when computing derivatives. Not used if no derivatives of theta are requested.

## Returns

The value (or derivative) of the Riemann theta function at each point in `zs`.
