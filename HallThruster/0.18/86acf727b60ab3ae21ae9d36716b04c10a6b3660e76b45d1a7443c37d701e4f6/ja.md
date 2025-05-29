```julia
alternate_field_names()

```

代替のasciiフィールド名と特殊文字を含むフィールド名とのマッピングの`NamedTuple`を返します。これらは、短い名前の代わりに`Solution`オブジェクトをインデックスする際に使用できます。

# 使用法

```jldoctest; setup = :(using HallThruster)
julia> HallThruster.alternate_field_names()
(mobility = :μ, potential = :ϕ, thermal_conductivity = :κ, grad_pe = :∇pe, nu_anom = :νan, nu_class = :νc, nu_wall = :νew_momentum, nu_ei = :νei, nu_en = :νen, nu_iz = :νiz, nu_ex = :νex, tan_divergence_angle = :tanδ)
```
