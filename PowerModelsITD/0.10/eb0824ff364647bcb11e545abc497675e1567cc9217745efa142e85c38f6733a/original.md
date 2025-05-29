```
function parse_files(
    pm_file::String,
    pmd_file::String,
    pmitd_file::String;
    multinetwork::Bool=false
    auto_rename::Bool=false
)
```

Parses PowerModels, PowerModelsDistribution, and PowerModelsITD boundary linkage input files and returns a data dictionary with the combined information of the inputted dictionaries.
