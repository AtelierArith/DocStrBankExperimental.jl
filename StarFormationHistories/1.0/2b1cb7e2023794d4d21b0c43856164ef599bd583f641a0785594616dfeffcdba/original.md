```
PowerLawMZR(α::Real, MH0::Real, logMstar0::Real=6,
            free::NTuple{2, Bool}=(true, true)) <: AbstractMZR
```

Mass-metallicity model described by a single power law index `α > 0`, a metallicity normalization `MH0`, and the logarithm of the stellar mass `logMstar0 = log10(Mstar0 [M⊙])` at which the mean metallicity is `MH0`. Because `logMstar0` and `MH0` are degenerate, we treat `MH0` as a fittable parameter and `logMstar0` as a fixed parameter that will not be changed during optimizations. Such a power law MZR is often used when extrapolating literature results to low masses, e.g., $\text{M}_* < 10^8 \; \text{M}_\odot.$ `α` will be fit freely during optimizations if `free[1] == true` and `MH0` will be fit freely if `free[2] == true`. The MZR is defined by

$$
\begin{aligned}
[\text{M} / \text{H}] \left( \text{M}_* \right) &= [\text{M} / \text{H}]_0 + \text{log} \left( \left( \frac{\text{M}_*}{\text{M}_{*,0}} \right)^\alpha \right) \\
&= [\text{M} / \text{H}]_0 + \alpha \, \left( \text{log} \left( \text{M}_* \right) - \text{log} \left( \text{M}_{*,0} \right) \right) \\
\end{aligned}
$$

# Examples

```jldoctest; setup=:(using StarFormationHistories: nparams, gradient, update_params, transforms, free_params)
julia> PowerLawMZR(1.0, -1) isa PowerLawMZR{Float64}
true

julia> import Test

julia> Test.@test_throws(ArgumentError, PowerLawMZR(-1.0, -1)) isa Test.Pass
true

julia> nparams(PowerLawMZR(1.0, -1)) == 2
true

julia> PowerLawMZR(1.0, -1, 6)(1e7) ≈ 0
true

julia> all(values(gradient(PowerLawMZR(1.0, -1, 6), 1e8)) .≈
                (2.0, 1.0, 1 / 1e8 / log(10)))
true

julia> update_params(PowerLawMZR(1.0, -1, 7, (true, false)), (2.0, -2)) ==
         PowerLawMZR(2.0, -2, 7, (true, false))
true

julia> transforms(PowerLawMZR(1.0, -1)) == (1,0)
true

julia> free_params(PowerLawMZR(1.0, -1, 7, (true, false))) == (true, false)
true
```
