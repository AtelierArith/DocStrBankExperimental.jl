```
distinguish_spin(projection_all::Projection,
    projection_axis::Projection,
    bands::Bands)
```

Distinguish projection of spin up and spin down. (Used in projection loaded from PROCAR)

# Arguments

  * `projection_all::Projection`: total projected magnetization
  * `projection_axis::Projection`: projected magnetization in x, y or z axis
  * `bands::Bands`: metadata of bands

# Returnss

  * `ProjectionWithSpin`: projection of spin up and spin down
  * `BandsWithSpin`: metadata of bands of spin up and spin down
