```
HyperbolicModel((V₁, ...), ((I₁₁, ...), ...), (mob₁, ...))
```

粒子システムを表します：

  * 外部速度 `Vᵢ`、
  * 統合された相互作用 `Iᵢⱼ`（これは種 `j` が種 `i` に与える影響です）、
  * 移動度 `mobᵢ`。

[`ParabolicModel`](@ref) も参照してください。

# 例

```jldoctest
julia> using ConservationLawsParticles.Examples, RecursiveArrayTools

julia> model = HyperbolicModel(
           (V, V),
           ((SampledInteraction(Wprime_attr), IntegratedInteraction(W_rep)),
            (IntegratedInteraction(W_rep), SampledInteraction(Wprime_attr))),
           (mobρ, mobσ));

julia> x = ArrayPartition(gaussian_particles(2, 4), collect(range(-3, 4, length=5)));

julia> round.(x; digits=2)
([-2.0, -0.3, 0.3, 2.0], [-3.0, -1.25, 0.5, 2.25, 4.0])

julia> abstract_velocities(x, model, 0.) .|> v -> round(v; digits=2)
([6.27, 0.26, -0.38, -6.56], [22.92, 0.82, 0.71, -8.68, -54.89])
```
