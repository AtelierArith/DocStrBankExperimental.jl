```
Outgoing <: ParticleDirection
```

具体的な[`ParticleDirection`](@ref)の実装で、特定のプロセスの文脈において粒子が*外向き*であることを示します。主にディスパッチに使用されます。

```jldoctest
julia> using QEDbase

julia> Outgoing()
outgoing
```

!!! note "ParticleDirection インターフェース"
    [`ParticleDirection`](@ref)のサブタイプであることに加えて、`Outgoing`は

    ```julia
    is_incoming(::Outgoing) = false
    is_outgoing(::Outgoing) = true
    ```

