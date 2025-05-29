```
parse_opendss(file::String; method::Union{String,Missing}=missing, kwargs...)
```

Parse opendss data file using PowerModelsDistribution parse_file function into an ENGINEERING data model adding some extra data transformations specific to fault studies.

`method` should be `missing` or `"PMD"`.

`kwargs` can be any valid keyword arguments from PowerModelsDistribution's `parse_file` function.
