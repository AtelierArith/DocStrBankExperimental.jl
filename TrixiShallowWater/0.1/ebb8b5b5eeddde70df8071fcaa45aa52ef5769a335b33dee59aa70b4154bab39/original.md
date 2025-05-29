```
dissipation_roe(u_ll, u_rr, orientation_or_normal_direction,
                                equations::ShallowWaterEquationsWetDry2D)
```

Roe-type dissipation term for the [`ShallowWaterEquationsWetDry2D`](@ref). To create the classical Roe solver, this dissipation term can be combined with [`Trixi.flux_central`](@extref) using [`Trixi.FluxPlusDissipation`](@extref).

For details on the Roe linearization see Chapter 15.3.2 and Chapter 21.7 for the two-dimensional shallow water equations of the book:

  * Randall J. LeVeque (2002) Finite Volume Methods for Hyperbolic Problems [DOI: 10.1017/CBO9780511791253](https://doi.org/10.1017/CBO9780511791253)
