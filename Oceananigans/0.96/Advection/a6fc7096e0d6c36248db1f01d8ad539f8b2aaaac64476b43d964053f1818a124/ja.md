```
WENOVectorInvariant(FT = Float64;
                    upwinding = nothing,
                    vorticity_stencil = VelocityStencil(),
                    order = nothing,
                    vorticity_order = nothing,
                    vertical_order = nothing,
                    divergence_order = nothing,
                    kinetic_energy_gradient_order = nothing,
                    multi_dimensional_stencil = false,
                    weno_kw...)
```

ベクトル不変重み付き本質的非振動（WENO）スキームを返します。キーワード引数の定義については[`VectorInvariant`](@ref)および[`WENO`](@ref)を参照してください。

`multi_dimensional_stencil = true`が選択されると、WENOスキームのために2D水平ステンシルが実装されます（1Dステンシルの代わりに）。この2D水平ステンシルは、上流方向に接する水平方向での渦度、発散、および運動エネルギーの中心5次WENO再構成を行います。
