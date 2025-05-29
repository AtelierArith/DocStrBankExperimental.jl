```julia
load_magnetic_field(
    file::String;
    include_dirs
) -> HallThruster.MagneticField

```

Given a path to a file, loads a `MagneticField` from the data in that file. Looks in the present working directory and any additional directories passed to `include_dirs`.
