```
load_file_line_by_line(filename::AbstractString) -> String[]
```

Load and return the content of the text file in `String[]`, i.e., one element for each line.

# Arguments

  * `filename::AbstractString`: the filename of the file to load,

# Keywords

# Returns

  * `String[]`: the array of the file content,

# Throws

  * `Error`: in the case of file does not exist.
