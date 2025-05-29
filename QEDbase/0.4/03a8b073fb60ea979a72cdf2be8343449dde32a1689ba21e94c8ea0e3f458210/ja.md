```
UnknownDirection <: ParticleDirection
```

[`ParticleDirection`](@ref) の具体的な実装で、粒子が未知の方向を持つことを示します。これは、特定の方向が与えられた文脈で意味を持たない、方向が利用できない、またはそれが不必要であることを意味する場合があります。

```jldoctest
julia> using QEDbase

julia> UnknownDirection()
unknown direction
```

!!! note "ParticleDirection インターフェース"
    `UnknownDirection` は [`ParticleDirection`](@ref) のサブタイプであるだけでなく、次のようなメソッドを持っています。

    ```julia
    is_incoming(::UnknownDirection) = false
    is_outgoing(::UnknownDirection) = false
    ```

