Abstract base type for anti-fermions as distinct from its particle counterpart `Fermion`.

!!! note "particle interface"
    All subtypes of `AntiFermion` have

    ```julia
    is_fermion(::AntiFermion) = true
    is_particle(::AntiFermion) = false
    is_anti_particle(::AntiFermion) = true
    ```

