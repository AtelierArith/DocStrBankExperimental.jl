Abstract base type for majorana-fermions, i.e. fermions which are their own anti-particles.

!!! note "particle interface"
    All subtypes of `MajoranaFermion` have

    ```julia
    is_fermion(::MajoranaFermion) = true
    is_particle(::MajoranaFermion) = true
    is_anti_particle(::MajoranaFermion) = true
    ```

