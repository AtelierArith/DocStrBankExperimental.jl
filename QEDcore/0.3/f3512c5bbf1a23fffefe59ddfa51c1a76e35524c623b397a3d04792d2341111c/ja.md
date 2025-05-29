反ボソンの抽象基本型であり、その粒子対応物 [`Boson`](@ref) とは異なる。

!!! note "粒子インターフェース"
    `AntiBoson` のすべてのサブタイプは次のようになります。

    ```julia
    is_boson(::AntiBoson) = true
    is_particle(::AntiBoson) = false
    is_anti_particle(::AntiBoson) = true
    ```

