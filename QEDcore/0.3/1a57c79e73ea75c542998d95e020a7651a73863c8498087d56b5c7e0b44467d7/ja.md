ボソンの抽象基本型であり、その反粒子の対応物 [`AntiBoson`](@ref) とは異なります。

!!! note "粒子インターフェース"
    `Boson` のすべてのサブタイプは次のようになります。

    ```julia
    is_boson(::Boson) = true
    is_particle(::Boson) = true
    is_anti_particle(::Boson) = false
    ```

