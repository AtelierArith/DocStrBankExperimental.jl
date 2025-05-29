```
record_struct_expression(file_name, record_type)
```

Function to autogenerate `Struct` code based on a CSV file.  Also autogenerates `get_description` and `get_scale_factor` method for `Struct`. Use it together with `eval`.

# Example

```julia-repl
julia> eval(record_struct_expression(joinpath(@__DIR__, "TEST_FORmaT.csv"), DataRecord))
julia> TEST_FORMAT <: DataRecord
true
```
