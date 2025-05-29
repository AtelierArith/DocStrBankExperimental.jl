Concrete type for *electrons* as a particle species. Mostly used for dispatch.

```jldoctest
julia> using QEDcore

julia> Electron()
electron
```

!!! note "particle interface"
    Besides being a subtype of [`Fermion`](@ref), objects of type `Electron` have

    ```julia
    mass(::Electron) = 1.0
    charge(::Electron) = -1.0
    ```

