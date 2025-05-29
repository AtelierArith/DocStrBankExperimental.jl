```julia
NonhomotheticCESUtility(σ, Ω̂s, ϵs)

```

Non-homothetic CES preferences, as defined in

*Comin, D., Lashkari, D., & Mestieri, Martí (2021). Structural change with long-run  income and price effects. Econometrica, 89(1), 311–374.*

### Definition

Let $E = ∑ᵢ pᵢ Cᵢ$ denote that *total expenditure*. The consumption aggregator `C` is defined implicitly by

$$
E^{1 - \sigma} = \sum_i \Omega_i (C^{\epsilon_i} p_i)^{1 - \sigma}
$$

In the actual calculation and parametrization, we use logs ($Ê = log(E)$ etc) for improved floating point accuracy.

### Arguments

  * `σ`: elasticity of substitution between goods of different sectors, `> 0`, `≠ 1`.
  * `Ω̂s`: **log** of sector weights
  * `ϵs`: sectoral non-homotheticity parameters.

### Suggestions

  * Use `SVector`s for vector arguments whenever possible.
  * You may want to normalize some normalize some way, eg to `ϵ = 1` and `Ω̂ = 0` for a *base good* as described in equation (10) of the paper.
