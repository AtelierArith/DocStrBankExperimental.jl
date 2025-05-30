```
ParabolicModel((V₁, ...), ((I₁₁, ...), ...), (mob₁, ...), (D₁, ...))
```

は次のような粒子系を表します：

  * 外部速度 `Vᵢ`、
  * 相互作用 `Iᵢⱼ`（これは種 `j` が種 `i` に与える影響です）、
  * 移動度 `mobᵢ`、
  * 拡散 `Dᵢ`。

詳細は [`HyperbolicModel`](@ref) を参照してください。

# 例

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
