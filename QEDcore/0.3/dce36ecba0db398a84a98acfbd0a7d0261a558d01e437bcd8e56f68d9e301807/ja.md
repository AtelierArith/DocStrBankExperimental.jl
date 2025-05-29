反フェルミオンの抽象基本型であり、その粒子対応物 `Fermion` とは異なります。

!!! note "粒子インターフェース"
    `AntiFermion` のすべてのサブタイプは

    ```julia
    is_fermion(::AntiFermion) = true
    is_particle(::AntiFermion) = false
    is_anti_particle(::AntiFermion) = true
    ```

