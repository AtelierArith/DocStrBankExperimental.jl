```
solps2imas(
    b2gmtry::String,
    b2output::String="";
    gsdesc::String=default_gsdesc,
    b2mn::String="",
    fort::Tuple{String, String, String}=("", "", ""),
    fort_tol::Float64=1e-6,
    b2_boundary_parameters::String="",
    load_bb::Bool=false,
)::IMASdd.dd
```

Main function of the module. Takes in a geometry file and an (optional) output file (either b2time or b2fstate) and a grid_ggd description in the form of a Dict or filename to equivalent YAML file. Additionally, EIRENE `fort` files can be provided as tuple of 3 filenames consisting fort.33, fort.34, and fort.35 files. The grids in these files are matched with SOLPS grid with a tolerance of `fort_tol` (defaults to 1e-6). Further settings can be loaded from b2.*.parameters files and equilibrium files.
