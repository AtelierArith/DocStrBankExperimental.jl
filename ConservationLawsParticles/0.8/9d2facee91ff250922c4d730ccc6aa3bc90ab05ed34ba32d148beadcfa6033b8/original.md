```
DiffusiveIntegratedModel((V₁, ...), ((W₁₁, ...), ...), (mob₁, ...), (D₁, ...))
```

Represents a particles system with:

  * external velocities `Vᵢ`,
  * integrated interactions `Wᵢⱼ` (this is the effect of the species `j` on the species `i`),
  * mobilities `mobᵢ`,
  * diffusions `Dᵢ`.

See also [`DiffusiveSampledModel`](@ref).

# Examples

```jldoctest
julia> using ConservationLawsParticles.Examples, RecursiveArrayTools

julia> model = DiffusiveIntegratedModel(
           (V, V),
           ((W_attr, W_rep),
            (W_rep, W_attr)),
           (mobρ, mobσ),
           (Diffusion(1), nothing));

julia> x = ArrayPartition(gaussian_particles(2, 4), collect(range(-3, 4, length=5)));

julia> round.(x; digits=2)
([-2.0, -0.3, 0.3, 2.0], [-3.0, -1.25, 0.5, 2.25, 4.0])

julia> velocities_diff(x, model, 0.) .|> v -> round(v; digits=2)
([6.03, -0.76, 0.63, -6.33], [23.26, 0.9, 0.71, -8.77, -55.23])
```
