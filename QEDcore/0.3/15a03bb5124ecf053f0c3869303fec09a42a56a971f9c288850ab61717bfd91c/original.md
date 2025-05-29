Concrete type for the *photons* as a particle species. Mostly used for dispatch.

```jldoctest
julia> using QEDcore

julia> Photon()
photon
```

!!! note "particle interface"
    Besides being a subtype of `MajoranaBoson`, `Photon` has

    ```julia
    mass(::Photon) = 0.0
    charge(::Photon) = 0.0
    ```

