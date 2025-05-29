```
load_table(
    file_path::String
    years::Int...;
)
```

Load a `WiNDCtable` from a file. 

## Required Arguments

  * `file_path::String`: The path to the file.
  * `years::Int...`: The years to load. If no years are provided, all years in the file   will be loaded.

## Returns

A subtype of a WiNDCtable, with the data and sets loaded from the file.
