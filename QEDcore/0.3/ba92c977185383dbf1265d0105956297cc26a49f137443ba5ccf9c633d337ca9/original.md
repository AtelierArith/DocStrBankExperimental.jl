Concrete type for *positrons* as a particle species. Mostly used for dispatch.

```jldoctest
julia> using QEDcore

julia> Positron()
positron
```

!!! note "particle interface"
    Besides being a subtype of [`AntiFermion`](@ref), objects of type `Positron` have

    ```julia
    mass(::Positron) = 1.0
    charge(::Positron) = 1.0
    ```

