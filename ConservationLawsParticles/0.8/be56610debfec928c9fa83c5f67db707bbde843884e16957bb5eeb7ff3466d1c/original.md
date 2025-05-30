```
ParabolicModel((V₁, ...), ((I₁₁, ...), ...), (mob₁, ...), (D₁, ...))
```

Represents a particles system with:

  * external velocities `Vᵢ`,
  * interactions `Iᵢⱼ` (this is the effect of the species `j` on the species `i`),
  * mobilities `mobᵢ`,
  * diffusions `Dᵢ`.

See also [`HyperbolicModel`](@ref).

# Examples

```jldoctest
julia> using ConservationLawsParticles.Examples, RecursiveArrayTools

julia> model = ParabolicModel(
           (V, V),
           ((SampledInteraction(Wprime_attr), IntegratedInteraction(W_rep)),
            (IntegratedInteraction(W_rep), SampledInteraction(Wprime_attr))),
           (mobρ, mobσ),
           (Diffusion(1), nothing));

julia> x = ArrayPartition(gaussian_particles(2, 4), collect(range(-3, 4, length=5)));

julia> round.(x; digits=2)
([-2.0, -0.3, 0.3, 2.0], [-3.0, -1.25, 0.5, 2.25, 4.0])

julia> abstract_velocities(x, model, 0.) .|> v -> round(v; digits=2)
([5.68, -0.8, 0.68, -5.97], [22.92, 0.82, 0.71, -8.68, -54.89])
```
