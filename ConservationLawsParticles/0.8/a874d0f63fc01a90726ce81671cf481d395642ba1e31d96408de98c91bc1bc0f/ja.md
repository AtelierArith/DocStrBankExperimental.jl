```
IntegratedModel((V₁, ...), ((W₁₁, ...), ...), (mob₁, ...))
```

粒子システムを表します：

  * 外部速度 `Vᵢ`、
  * 統合された相互作用 `Wᵢⱼ`（これは種 `j` が種 `i` に与える影響です）、
  * 移動度 `mobᵢ`。

[`SampledModel`](@ref) も参照してください。

# 例

```jldoctest
julia> using ConservationLawsParticles.Examples, RecursiveArrayTools

julia> model = IntegratedModel(
           (V, V),
           ((W_attr, W_rep),
            (W_rep, W_attr)),
           (mobρ, mobσ));

julia> x = ArrayPartition(gaussian_particles(2, 4), collect(range(-3, 4, length=5)));

julia> round.(x; digits=2)
([-2.0, -0.3, 0.3, 2.0], [-3.0, -1.25, 0.5, 2.25, 4.0])

julia> velocities(x, model, 0.) .|> v -> round(v; digits=2)
([6.62, 0.31, -0.43, -6.91], [23.26, 0.9, 0.71, -8.77, -55.23])
```
