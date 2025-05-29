Concrete type which indicates, that a particle with [`is_boson`](@ref) has polarization in $x$-direction.

```jldoctest
julia> using QEDbase

julia> PolX()
x-polarized
```

!!! note "Coordinate axes"
    The notion of axes, e.g. $x$- and $y$-direction is just to distinguish two orthogonal polarization directions. However, if the three-momentum of the particle with [`is_boson`](@ref) is aligned to the $z$-axis of a coordinate system, the polarization axes define the $x$- or $y$-axis, respectively.


!!! info "Alias"
    There is a built-in alias for `PolarizationX`:

    ```jldoctest
    julia> using QEDbase

    julia> PolarizationX === PolX
    true
    ```

