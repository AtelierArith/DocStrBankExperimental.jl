```julia
Directory(directory::String, glob_pattern::String; second_in_pair = nothing)
```

List all files matching the `glob_pattern` (See [Glob.jl](https://github.com/vtjnash/Glob.jl)) in `directory`. For paired files a function taking as argument the filename of the first file in pair and returning the filename of the second file can be provided.

```@example
Directory(input_directory, "*.fastq")
```
