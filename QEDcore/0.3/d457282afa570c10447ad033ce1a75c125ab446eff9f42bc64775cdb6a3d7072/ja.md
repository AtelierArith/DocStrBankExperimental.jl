フェルミオンの抽象基本型であり、[`AntiFermion`](@ref)とは異なります。

!!! note "粒子インターフェース"
    `Fermion`のすべてのサブタイプは次のようになります。

    ```julia
    is_fermion(::Fermion) = true
    is_particle(::Fermion) = true
    is_anti_particle(::Fermion) = false
    ```

