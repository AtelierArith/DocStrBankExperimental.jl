```
add_arg_table!(settings, [arg_name [,arg_options]]...)
```

This function is very similar to the macro version [`@add_arg_table!`](@ref). Its syntax is stricter: tuples and blocks are not allowed and argument options are explicitly specified as `Dict` objects. However, since it doesn't involve macros, it offers more flexibility in other respects, e.g. the `arg_name` entries need not be explicit, they can be anything which evaluates to a `String` or a `Vector{String}`.

Example:

```julia
add_arg_table!(settings,
    ["--opt1", "-o"],
    Dict(
        :help => "an option with an argument"
    ),
    "--opt2",
    "arg1",
    Dict(
        :help => "a positional argument"
        :required => true
    ))
```
