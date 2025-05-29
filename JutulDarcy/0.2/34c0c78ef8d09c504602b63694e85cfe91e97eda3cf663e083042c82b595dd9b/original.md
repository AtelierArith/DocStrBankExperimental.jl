```
case = setup_case_from_data_file(
    filename;
    parse_arg = NamedTuple(),
    kwarg...
)

case, data = setup_case_from_data_file(filename; include_data = true)
```

Set up a [`JutulCase`](@ref) from a standard input file (with extension .DATA). Additional arguments to the parser can be passed as key/values in a `NamedTuple` given as `parse_arg`. The optional input `include_data=true` will make the function return the parsed data in addition the case itself. Additional keyword arguments are passed on to [`setup_case_from_parsed_data`](@ref).
