```
add_arg_group!(settings, description, [name , [set_as_default]]; keywords...)
```

This function adds an argument group to the argument table in `settings`. The `description` is a `String` used in the help screen as a title for that group. The `name` is a unique name which can be provided to refer to that group at a later time.

Groups can be declared to be mutually exclusive and/or required, see below.

After invoking this function, all subsequent invocations of the [`@add_arg_table!`](@ref) macro and [`add_arg_table!`](@ref) function will use the new group as the default, unless `set_as_default` is set to `false` (the default is `true`, and the option can only be set if providing a `name`). Therefore, the most obvious usage pattern is: for each group, add it and populate the argument table of that group. Example:

```julia-repl
julia> settings = ArgParseSettings();

julia> add_arg_group!(settings, "custom group");

julia> @add_arg_table! settings begin
          "--opt"
          "arg"
       end;

julia> parse_args(["--help"], settings)
usage: <command> [--opt OPT] [-h] [arg]

optional arguments:
  -h, --help  show this help message and exit

custom group:
  --opt OPT
  arg
```

As seen from the example, new groups are always added at the end of existing ones.

The `name` can also be passed as a `Symbol`. Forbidden names are the standard groups names (`"command"`, `"positional"` and `"optional"`) and those beginning with a hash character `'#'`.

In order to declare a group as mutually exclusive, use the keyword `exclusive = true`. Mutually exclusive groups can only contain options, not arguments nor commands, and parsing will fail if more than one option from the group is provided.

A group can be declared as required using the `required = true` keyword, in which case at least one option or positional argument or command from the group must be provided.
