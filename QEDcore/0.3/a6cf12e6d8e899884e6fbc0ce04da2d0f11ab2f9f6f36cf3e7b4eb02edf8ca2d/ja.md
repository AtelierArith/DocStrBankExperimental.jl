マヨラナボソンのための抽象基本型、すなわち自分自身の反粒子であるボソン。

!!! note "粒子インターフェース"
    `MajoranaBoson` のすべてのサブタイプは次のようになります。

    ```julia
    is_boson(::MajoranaBoson) = true
    is_particle(::MajoranaBoson) = true
    is_anti_particle(::MajoranaBoson) = true
    ```

