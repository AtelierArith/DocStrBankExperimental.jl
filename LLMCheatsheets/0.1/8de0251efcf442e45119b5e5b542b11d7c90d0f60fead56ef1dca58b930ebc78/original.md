```
collate_files(file_contents::AbstractVector{<:AbstractDict})
```

Collates the file contents into a single string.

# Arguments

  * `file_contents::AbstractVector{<:AbstractDict}`: The contents of the files in the repository. Requires `:name` and `:content` fields.

# Returns

  * `String`: A string with the concatenated file names and contents.
