Concrete type indicating that a particle with [`is_boson`](@ref) has an indefinite polarization and the differential cross section calculation should average or sum over all polarizations, depending on the direction ([`Incoming`](@ref) or [`Outgoing`](@ref)) of the particle in question.

```jldoctest
julia> using QEDbase

julia> AllPol()
all polarizations
```

!!! info "Alias"
    There is a built-in alias for `AllPolarization`:

    ```jldoctest
    julia> using QEDbase

    julia> AllPolarization === AllPol
    true
    ```

