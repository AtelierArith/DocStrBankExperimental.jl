```
get_gem_dataframe_from_cdc_gem_txt(path_to_txt::String, direction::String)
```

Get a `GEM{DataFrame}` object from a .txt file as downloaded from the [CDC website](https://ftp.cdc.gov/pub/Health_Statistics/NCHS/Publications/ICD10CM/2018/Dxgem_2018.zip). `path_to_txt` is the path to the .txt file, while `direction` is the direction of the GEM file (either `"I9_I10"` or `"I10_I9"`, see [`GEM`](@ref)).
