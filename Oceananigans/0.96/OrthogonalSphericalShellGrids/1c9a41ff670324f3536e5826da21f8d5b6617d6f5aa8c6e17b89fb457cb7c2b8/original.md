```
TripolarGrid(arch = CPU(), FT::DataType = Float64;
             size,
             southernmost_latitude = -80,
             halo = (4, 4, 4),
             radius = R_Earth,
             z = (0, 1),
             north_poles_latitude = 55,
             first_pole_longitude = 70)
```

Return an `OrthogonalSphericalShellGrid` tripolar grid on the sphere. The tripolar grid replaces the North pole singularity with two other singularities at `north_poles_latitude` that is *less* than 90ᵒ.

# Positional Arguments

  * `arch`: The architecture to use for the grid. Default is `CPU()`.
  * `FT::DataType`: The data type to use for the grid. Default is `Float64`.

# Keyword Arguments

  * `size`: The number of cells in the (longitude, latitude, vertical) dimensions.
  * `southernmost_latitude`: The southernmost `Center` latitude of the grid. Default is -80.
  * `halo`: The halo size in the (longitude, latitude, vertical) dimensions. Default is (4, 4, 4).
  * `radius`: The radius of the spherical shell. Default is `R_Earth`.
  * `z`: The vertical $z$-coordinate range of the grid. Default is (0, 1).
  * `first_pole_longitude`: The longitude of the first "north" singularity.                         The second singularity is located at `first_pole_longitude + 180ᵒ`.
  * `north_poles_latitude`: The latitude of the "north" singularities.

!!! warning "Longitude coordinate must have even number of cells"
    `size` is a 3-tuple of the grid size in longitude, latitude, and vertical directions. Due to requirements of the folding at the north edge of the domain, the longitude size of the grid (i.e., the first component of `size`) *must* be an even number!


!!! info "North pole singularities"
    The north singularities are located at: `i = 1`, `j = Nφ` and `i = Nλ ÷ 2 + 1`, `j = Nφ`.

