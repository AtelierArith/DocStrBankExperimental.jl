```julia
load_magnetic_field!(
    magnetic_field::HallThruster.MagneticField;
    include_dirs
)

```

Given a magnetic field `field` with empty `z` or `B` fields, looks for a magnetic field at `field`.file. If one is found in the present directory or in any of the provided `include_dirs`, sets `z` and `B` accordingly. Throws an ArgumentError if one is not found.
