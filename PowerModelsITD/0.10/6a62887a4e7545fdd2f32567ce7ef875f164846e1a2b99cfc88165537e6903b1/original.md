```
function parse_power_distribution_file(
    pmd_file::String,
    base_data::Dict{String,<:Any}=Dict{String, Any}();
    unique::Bool=true,
    multinetwork::Bool=false,
    auto_rename::Bool=false,
    ms_num::Int=1
)
```

Parses power distribution files from the file `pmd_file` depending on the file extension. `base_data` represents a dictionary that contains data from other pmd systems (serving as the base where all data will be combined), `unique` represents if the pmd data provided is the first one passed or unique. If it is not `unique`, then the components need to be renamed before being added. Returns a PowerModelsDistribution data structured pmd network (a dictionary) with renamed components (if applicable).
