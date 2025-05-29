Concrete type which indicates, that a particle with [`is_boson`](@ref) has polarization in $y$-direction.

```jldoctest
julia> using QEDbase

julia> PolY()
y-polarized
```

!!! note "Coordinate axes"
    The notion of axes, e.g. $x$- and $y$-direction is just to distinguish two orthogonal polarization directions. However, if the three-momentum of the particle with [`is_boson`](@ref) is aligned to the $z$-axis of a coordinate system, the polarization axes define the $x$- or $y$-axis, respectively.


!!! info "Alias"
    There is a built-in alias for `PolarizationY`:

    ```jldoctest
    julia> using QEDbase

    julia> PolarizationY === PolY
    true
    ```

