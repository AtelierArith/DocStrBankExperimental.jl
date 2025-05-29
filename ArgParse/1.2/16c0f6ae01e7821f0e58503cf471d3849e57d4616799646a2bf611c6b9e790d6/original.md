```
parse_args([args,] settings; as_symbols::Bool = false)
```

This is the central function of the `ArgParse` module. It takes a `Vector` of arguments and an [`ArgParseSettings`](@ref) object, and returns a `Dict{String,Any}`. If `args` is not provided, the global variable `ARGS` will be used.

When the keyword argument `as_symbols` is `true`, the function will return a `Dict{Symbol,Any}` instead.

The returned `Dict` keys are defined (possibly implicitly) in `settings`, and their associated values are parsed from `args`. Special keys are used for more advanced purposes; at the moment, one such key exists: `%COMMAND%` (`_COMMAND_` when using `as_symbols=true`; see the [Commands](@ref) section).

Arguments are parsed in sequence and matched against the argument table in `settings` to determine whether they are long options, short options, option arguments or positional arguments:

  * long options begin with a double dash `"--"`; if a `'='` character is found, the remainder is the option argument; therefore, `["--opt=arg"]` and `["--opt", "arg"]` are equivalent if `--opt` takes at least one argument. Long options can be abbreviated (e.g. `--opt` instead of `--option`) as long as there is no ambiguity.
  * short options begin with a single dash `"-"` and their name consists of a single character; they can be grouped together (e.g. `["-x", "-y"]` can become `["-xy"]`), but in that case only the last option in the group can take an argument (which can also be grouped, e.g. `["-a", "-f", "file.txt"]` can be passed as `["-affile.txt"]` if `-a` does not take an argument and `-f` does). The `'='` character can be used to separate option names from option arguments as well (e.g. `-af=file.txt`).
  * positional arguments are anything else; they can appear anywhere.

The special string `"--"` can be used to signal the end of all options; after that, everything is considered as a positional argument (e.g. if `args = ["--opt1", "--", "--opt2"]`, the parser will recognize `--opt1` as a long option without argument, and `--opt2` as a positional argument).

The special string `"-"` is always parsed as a positional argument.

The parsing can stop early if a `:show_help` or `:show_version` action is triggered, or if a parsing error is found.

Some ambiguities can arise in parsing, see the [Parsing details](@ref) section for a detailed description of how they're solved.
