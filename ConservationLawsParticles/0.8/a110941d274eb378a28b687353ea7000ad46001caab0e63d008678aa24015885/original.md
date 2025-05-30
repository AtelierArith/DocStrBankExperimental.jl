```
SampledModel((V₁, ...), ((W′₁₁, ...), ...), (mob₁, ...))
```

Represents a particles system with:

  * external velocities `Vᵢ`,
  * sampled interactions `W′ᵢⱼ` (this is the effect of the species `j` on the species `i`),
  * mobilities `mobᵢ`.

See also [`IntegratedModel`](@ref).

# Examples

```jldoctest
julia> using ConservationLawsParticles.Examples, RecursiveArrayTools

julia> model = SampledModel(
           (V, V),
           ((Wprime_attr, Wprime_rep),
            (Wprime_rep, Wprime_attr)),
           (mobρ, mobσ));

julia> x = ArrayPartition(gaussian_particles(2, 4), collect(range(-3, 4, length=5)));

julia> round.(x; digits=2)
([-2.0, -0.3, 0.3, 2.0], [-3.0, -1.25, 0.5, 2.25, 4.0])

julia> velocities(x, model, 0.) .|> v -> round(v; digits=2)
([6.29, 0.25, -0.72, -7.23], [22.41, 1.12, 1.52, -7.87, -54.54])
```
