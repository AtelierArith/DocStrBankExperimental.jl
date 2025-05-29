```
@add_arg_table!(settings, table...)
```

This macro adds a table of arguments and options to the given `settings`. It can be invoked multiple times. The arguments groups are determined automatically, or the current default group is used if specified (see the [Argument groups](@ref) section for more details).

The `table` is a list in which each element can be either `String`, or a tuple or a vector of `String`, or an assigmment expression, or a block:

  * a `String`, a tuple or a vector introduces a new positional argument or option. Tuples and vectors are only allowed for options or commands, and provide alternative names (e.g. `["--opt", "-o"]` or `["checkout", "co"]`)
  * assignment expressions (i.e. expressions using `=`, `:=` or `=>`) describe the previous argument behavior (e.g.  `help = "an option"` or `required => false`).  See the [Argument entry settings](@ref) section for a complete description
  * blocks (`begin...end` or lists of expressions in parentheses separated by semicolons) are useful to group entries and span multiple lines.

These rules allow for a variety usage styles, which are discussed in the [Argument table styles](@ref) section. In the rest of the documentation, we will mostly use this style:

```julia
@add_arg_table! settings begin
    "--opt1", "-o"
        help = "an option with an argument"
    "--opt2"
    "arg1"
        help = "a positional argument"
        required = true
end
```

In the above example, the `table` is put in a single `begin...end` block and the line `"--opt1", "-o"` is parsed as a tuple; indentation is used to help readability.

See also the function [`add_arg_table!`](@ref).
