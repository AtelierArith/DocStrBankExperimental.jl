Abstract base type for fermions as distinct from [`AntiFermion`](@ref)s.

!!! note "particle interface"
    All subtypes of `Fermion` have

    ```julia
    is_fermion(::Fermion) = true
    is_particle(::Fermion) = true
    is_anti_particle(::Fermion) = false
    ```

