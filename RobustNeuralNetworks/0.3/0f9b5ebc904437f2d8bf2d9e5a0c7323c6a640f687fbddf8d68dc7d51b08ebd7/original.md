```
DirectRENParams{T}(nu, nx, nv; <keyword arguments>) where T
```

Construct direct parameterisation for an (acyclic) recurrent equilibrium network.

This is typically used by higher-level constructors when defining a REN, which take the direct parameterisation and define rules for converting it to an explicit parameterisation. See for example [`GeneralRENParams`](@ref).

# Arguments

  * `nu::Int`: Number of inputs.
  * `nx::Int`: Number of states.
  * `nv::Int`: Number of neurons.

# Keyword arguments

  * `init=:randomQR`: Initialisation method. Options are:

      * `:random`: Random sampling with Glorot normal distribution. Typically samples "faster"/short memory dynamic models.
      * `:randomQR:` Compute `X` with `glorot_normal` and take the QR decomposition `X = qr(X).Q`. Good for initialising `X` close to the identity when long memory is needed. Default as legacy.
      * `:cholesky`: Compute `X` with cholesky factorisation of `H`, sets `E,F,P = I`. Good for slow/long memory dynamic models.
  * `polar_param::Bool=true`: Use polar parameterisation to construct `H` matrix from `X` in REN parameterisation (recommended).
  * `D22_free::Bool=false`: Specify whether to train `D22` as a free parameter (`true`), or construct it separately from `X3, Y3, Z3` (`false`). Typically use `D22_free = true` only for a contracting REN.
  * `D22_zero::Bool=false`: Fix `D22 = 0` to remove any feedthrough.
  * `bx_scale::T=0`: Set scale of initial state bias vector `bx`.
  * `bv_scale::T=1`: Set scalse of initial neuron input bias vector `bv`.
  * `output_map::Bool=true`: Include output layer $y_t = C_2 x_t + D_{21} w_t + D_{22} u_t + b_y$. Otherwise, output is just $y_t = x_t$.
  * `ϵ::T=1e-12`: Regularising parameter for positive-definite matrices.
  * `rng::AbstractRNG=Random.GLOBAL_RNG`: rng for model initialisation.

See [Revay et al. (2021)](https://arxiv.org/abs/2104.05942) for parameterisation details.

See also [`GeneralRENParams`](@ref), [`ContractingRENParams`](@ref), [`LipschitzRENParams`](@ref), [`PassiveRENParams`](@ref).
