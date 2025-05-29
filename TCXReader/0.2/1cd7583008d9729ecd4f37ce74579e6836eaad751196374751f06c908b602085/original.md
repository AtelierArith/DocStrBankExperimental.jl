```
loadTCXFile(filepath::String, csv_filepath::Union{String,Nothing}=nothing)
```

Load a TCX file and parse its contents.

# Arguments

  * `filepath`: The path to the TCX file.
  * `csv_filepath`: Optional. If provided, the parsed data will be exported to this CSV file.

# Returns

  * A tuple containing the parsed `TCXAuthor` and a vector of `TCXActivity` objects.
