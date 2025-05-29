```
parseABF(super_folder::String; extension::String=".abf")
```

Recursively search for ABF files in a directory and its subdirectories.

# Arguments

  * `super_folder`: Root directory to start the search
  * `extension`: File extension to search for (default: ".abf")

# Returns

  * Vector of file paths to all found ABF files

# Examples

```julia
# Find all ABF files in current directory and subdirectories
files = parseABF(".")

# Find files with custom extension
files = parseABF("data/", extension=".dat")

# Process multiple files
for file in parseABF("experiment_data/")
    exp = readABF(Float32, file)
    process_experiment(exp)
end
```

# Throws

  * `ArgumentError`: If no matching files are found in the directory

See also: [`readABF`](@ref)
