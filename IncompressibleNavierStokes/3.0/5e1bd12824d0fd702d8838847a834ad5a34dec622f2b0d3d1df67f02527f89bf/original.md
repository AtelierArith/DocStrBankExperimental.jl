```julia
temperature_equation(
;
    Pr,
    Ra,
    Ge,
    dodissipation,
    boundary_conditions,
    gdir,
    nondim_type
)

```

Create temperature equation setup (stored in a named tuple).

The equation is parameterized by three dimensionless numbers (Prandtl number, Rayleigh number, and Gebhart number), and requires separate boundary conditions for the `temperature` field. The `gdir` keyword specifies the direction gravity, while `non_dim_type` specifies the type of non-dimensionalization.
