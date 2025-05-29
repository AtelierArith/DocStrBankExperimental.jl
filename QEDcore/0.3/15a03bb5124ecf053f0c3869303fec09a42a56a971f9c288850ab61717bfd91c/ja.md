*光子*の粒子種としての具体的な型。主にディスパッチに使用されます。

```jldoctest
julia> using QEDcore

julia> Photon()
photon
```

!!! note "粒子インターフェース"
    `MajoranaBoson`のサブタイプであることに加えて、`Photon`は以下を持っています。

    ```julia
    mass(::Photon) = 0.0
    charge(::Photon) = 0.0
    ```

