```
get_snap_numbers(
    expdir::String,
    expname::String="none"
    ;
    findall::Bool=false,
    filenames::Vector{String}=String[]
    )
```

Finds all files in the format 'expname*XXX.snap' in the experiment directory `exp*dir`, and returns a vector of the snapshots XXX. If`expname` is not given, is is assumed that the directory of the simulation matches the experiment name.
