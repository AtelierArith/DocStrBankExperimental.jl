```
judiIllumination(model; mode="u", k=1, recompute=true)
```

# Arguments

  * `model`: JUDI Model structure
  * `mode`: Type of ilumination, choicees of ("u", "v", "uv")
  * `k`: Power of the illumination, real number
  * `recompute`: Flag whether to recompute the illumination at each new propagation (Defaults to true)

    judiIllumination(F; mode="u", k=1, recompute=true)

# Arguments

  * `F`: JUDI propagator
  * `mode`: Type of ilumination, choicees of ("u", "v", "uv")
  * `k`: Power of the illumination, real positive number
  * `recompute`: Flag whether to recompute the illumination at each new propagation  (Defaults to true)

Diagonal approximation of the FWI Hessian as the energy of the wavefield. The diagonal contains the sum over time of the wavefield chosen as `mode`.

Options for the mode are "u" for the forward wavefield illumination, "v" for the adjoint wavefield illumination, and  "uv" for the pointwise product of the forward and adjoint wavefields illuminations. Additionally, the parameter "k" provides control on the scaling of the daiagonal raising it to the power `k`. 

# Example

I = judiIllumination(model) 

Construct the diagonal operator such that I*x = x ./ |||u||_2^2
