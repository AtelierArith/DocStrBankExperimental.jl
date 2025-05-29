```
Incoming <: ParticleDirection
```

具体的な[`ParticleDirection`](@ref)の実装で、特定のプロセスの文脈において粒子が*入ってくる*ことを示します。主にディスパッチに使用されます。

```jldoctest
julia> using QEDbase

julia> Incoming()
incoming
```

!!! note "ParticleDirection インターフェース"
    [`ParticleDirection`](@ref)のサブタイプであることに加えて、`Incoming`は

    ```julia
    is_incoming(::Incoming) = true
    is_outgoing(::Incoming) = false
    ```

