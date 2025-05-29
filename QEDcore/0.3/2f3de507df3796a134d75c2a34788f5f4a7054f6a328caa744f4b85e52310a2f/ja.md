マヨラナフェルミオンのための抽象基本型、すなわち自分自身の反粒子であるフェルミオン。

!!! note "粒子インターフェース"
    `MajoranaFermion`のすべてのサブタイプは

    ```julia
    is_fermion(::MajoranaFermion) = true
    is_particle(::MajoranaFermion) = true
    is_anti_particle(::MajoranaFermion) = true
    ```

