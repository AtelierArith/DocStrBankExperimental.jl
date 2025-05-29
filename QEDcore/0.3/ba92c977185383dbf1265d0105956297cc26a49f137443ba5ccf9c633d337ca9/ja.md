*陽電子*という粒子種の具体的な型。主にディスパッチに使用されます。

```jldoctest
julia> using QEDcore

julia> Positron()
positron
```

!!! note "粒子インターフェース"
    [`AntiFermion`](@ref)のサブタイプであることに加えて、`Positron`型のオブジェクトは

    ```julia
    mass(::Positron) = 1.0
    charge(::Positron) = 1.0
    ```

