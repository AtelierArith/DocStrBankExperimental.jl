```
θchoice(θz, bias, lapse) <: DDMθ
```

Fields:

  * `θz`: is a module-defined type that contains the parameters related to the latent variable model.
  * `bias` is the choice bias parameter.
  * `lapse` is the lapse parameter.

Example:

```julia
θchoice(θz=θz(σ2_i = 0.5, B = 15., λ = -0.5, σ2_a = 50., σ2_s = 1.5,
    ϕ = 0.8, τ_ϕ = 0.05), bias=1., lapse=0.05)
```
