*電子*という粒子種の具体的な型。主にディスパッチに使用されます。

```jldoctest
julia> using QEDcore

julia> Electron()
electron
```

!!! note "粒子インターフェース"
    [`Fermion`](@ref) のサブタイプであることに加えて、`Electron` 型のオブジェクトは

    ```julia
    mass(::Electron) = 1.0
    charge(::Electron) = -1.0
    ```

