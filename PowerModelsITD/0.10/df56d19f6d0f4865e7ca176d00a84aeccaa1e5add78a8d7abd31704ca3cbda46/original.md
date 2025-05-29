```
function parse_files(
    pm_file::String,
    pmd_files::Vector,
    pmitd_file::String;
    multinetwork::Bool=false,
    auto_rename::Bool=false
)
```

Parses PowerModels, PowerModelsDistribution vector, and PowerModelsITD linkage input files and returns a data dictionary with the combined information of the inputted dictionaries.
