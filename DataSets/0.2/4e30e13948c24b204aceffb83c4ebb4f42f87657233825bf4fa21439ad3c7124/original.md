```
dataset(name)
dataset(project, name)
```

Returns the [`DataSet`](@ref) with the given `name` from `project`. If omitted, the global data environment [`DataSets.PROJECT`](@ref) will be used.

The `DataSet` is *metadata*, but to use the actual *data* in your program you need to use the `open` function to access the `DataSet`'s content as a given Julia type.

# Example

To open a dataset named `"a_text_file"` and read the whole content as a String,

```julia
content = open(String, dataset("a_text_file"))
```

To open the same dataset as an `IO` stream and read only the first line,

```julia
open(IO, dataset("a_text_file")) do io
    line = readline(io)
    @info "The first line is" line
end
```

To open a directory as a browsable tree object,

```julia
open(BlobTree, dataset("a_tree_example"))
```
