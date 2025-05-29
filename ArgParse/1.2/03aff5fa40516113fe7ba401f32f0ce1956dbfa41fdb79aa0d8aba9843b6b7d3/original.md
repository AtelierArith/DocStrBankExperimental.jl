```
set_default_arg_group!(settings, [name])
```

Set the default group for subsequent invocations of the [`@add_arg_table!`](@ref) macro and [`add_arg_table!`](@ref) function. `name` is a `String`, and must be one of the standard group names (`"command"`, `"positional"` or `"optional"`) or one of the user-defined names given in `add_arg_group!` (groups with no assigned name cannot be used with this function).

If `name` is not provided or is the empty string `""`, then the default behavior is reset (i.e. arguments will be automatically assigned to the standard groups). The `name` can also be passed as a `Symbol`.
