```julia
mutable struct MagneticField
```

Specifies the radial magnetic field of a Hall thruster, measured along channel centerline.

# Fields

  * `file::String`: The file where magnetic field information can be found. Can be left empty if `z` and `B` are explicitly specified.

  * `z::Vector{Float64}`: The axial coordinates at which the magnetic field is known, in meters.

  * `B::Vector{Float64}`: The magnetic field at each point in `z`, measured in Teslas.
