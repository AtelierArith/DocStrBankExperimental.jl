```
function parse_power_transmission_file(
    pm_file::String;
    skip_correct::Bool = true,
    multinetwork::Bool=false,
    number_multinetworks::Int=0
)
```

Parses a power transmission file from the file `pm_file` and returns a PowerModels data structured pm network dictionary.
