Abstract base type for bosons as distinct from its anti-particle counterpart [`AntiBoson`](@ref).

!!! note "particle interface"
    All subtypes of `Boson` have

    ```julia
    is_boson(::Boson) = true
    is_particle(::Boson) = true
    is_anti_particle(::Boson) = false
    ```

