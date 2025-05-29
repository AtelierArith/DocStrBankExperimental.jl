```julia
run_simulation(
    json_file::String;
    restart
) -> HallThruster.Solution{_A, P, C} where {_A, P<:NamedTuple, C<:HallThruster.Config}

```

Run a simulation from a JSON input file. If `postprocess` is set in the JSON file and `postprocess.output_file` is non-empty, output will be written to `postprocess.output_file`. If `restart` is a JSON file, this function will also try to restart the simulation from that file. Returns a `Solution` object.
