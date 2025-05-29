Abstract base type for anti-bosons as distinct from its particle counterpart [`Boson`](@ref).

!!! note "particle interface"
    All subtypes of `AntiBoson` have

    ```julia
    is_boson(::AntiBoson) = true
    is_particle(::AntiBoson) = false
    is_anti_particle(::AntiBoson) = true
    ```

