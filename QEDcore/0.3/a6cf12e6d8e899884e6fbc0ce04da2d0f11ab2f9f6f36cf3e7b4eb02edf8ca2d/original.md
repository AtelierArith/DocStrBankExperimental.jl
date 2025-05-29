Abstract base type for majorana-bosons, i.e. bosons which are their own anti-particles.

!!! note "particle interface"
    All subtypes of `MajoranaBoson` have

    ```julia
    is_boson(::MajoranaBoson) = true
    is_particle(::MajoranaBoson) = true
    is_anti_particle(::MajoranaBoson) = true
    ```

