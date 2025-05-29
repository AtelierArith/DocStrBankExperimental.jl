```
ArgParseSettings
```

The `ArgParseSettings` object contains all the settings to be used during argument parsing. Settings are divided in two groups: general settings and argument-table-related settings. While the argument table requires specialized functions such as [`@add_arg_table!`](@ref) to be defined and manipulated, general settings are simply object fields (most of them are `Bool` or `String`) and can be passed to the constructor as keyword arguments, or directly set at any time.

This is the list of general settings currently available:

  * `prog` (default = `""`): the name of the program, as displayed in the auto-generated help and usage screens. If left empty, the source file name will be used.
  * `description` (default = `""`): a description of what the program does, to be displayed in the auto-generated help-screen, between the usage lines and the arguments description. If `preformatted_description` is `false` (see below), it will be automatically formatted, but you can still force newlines by using two consecutive newlines in the string, and manually control spaces by using non-breakable spaces (the character `'\ua0'`).
  * `preformatted_description` (default = `false`): disable automatic formatting of `description`.
  * `epilog` (default = `""`): like `description`, but will be displayed at the end of the help-screen, after the arguments description. The same formatting rules also apply.
  * `preformatted_epilog` (default = `false`): disable automatic formatting of `epilog`.
  * `usage` (default = `""`): the usage line(s) to be displayed in the help screen and when an error is found during parsing. If left empty, it will be auto-generated.
  * `version` (default = `"Unknown version"`): version information. It's used by the `:show_version` action.
  * `add_help` (default = `true`): if `true`, a `--help, -h` option (triggering the `:show_help` action) is added to the argument table.
  * `add_version` (default = `false`): if `true`, a `--version` option (triggering the `:show_version` action) is added to the argument table.
  * `help_width` (default = `70`): set the width of the help text. This does not affect the `usage` line if it is provided by the user rather than being auto-generated; it also does not affect the `description/epilog` lines if the `preformatted_description/epilog` options are set to `false`.
  * `help_alignment_width` (default = `24`): set the maximum width of the left column of the help text, where options and arguments names are listed. This also affects the indentation of the usage line when it is auto-generated. It must be ≥ 4 and should be less than `help_width`.
  * `fromfile_prefix_chars` (default = `Set{Char}()`): an argument beginning with one of these characters will specify a file from which arguments will be read, one argument read per line. Alphanumeric characters and the hyphen-minus (`'-'`) are prohibited.
  * `autofix_names` (default = `false`): if `true`, will try to automatically fix the uses of dashes (`'-'`) and underscores (`'_'`) in option names and destinations: all underscores will be converted to dashes in long option names; also, associated destination names, if auto-generated (see the [Argument names](@ref) section), will have dashes replaced with underscores, both for long options and for positional arguments. For example, an option declared as `"--my-opt"` will be associated with the key `"my_opt"` by default. It is especially advisable to turn this option on then parsing with the `as_symbols=true` argument to `parse_args`.
  * `error_on_conflict` (default = `true`): if `true`, throw an error in case conflicting entries are added to the argument table; if `false`, later entries will silently take precedence. See the [Conflicts and overrides](@ref) srction for a detailed description of what conflicts are and what is the exact behavior when this setting is `false`.
  * `suppress_warnings` (default = `false`): if `true`, all warnings will be suppressed.
  * `allow_ambiguous_opts` (default = `false`): if `true`, ambiguous options such as `-1` will be accepted.
  * `commands_are_required` (default = `true`): if `true`, commands will be mandatory. See the [Commands](@ref) section.
  * `exc_handler` (default = `ArgParse.default_handler`): this is a function which is invoked when an error is detected during parsing (e.g. an option is not recognized, a required argument is not passed etc.). It takes two arguments: the `settings::ArgParseSettings` object and the `err::ArgParseError` exception. The default handler behaves differently depending on whether it's invoked from a script or in an interactive environment (e.g. REPL/IJulia). In non-interactive (script) mode, it calls `ArgParse.cmdline_handler`, which prints the error text and the usage screen on standard error and exits Julia with error code 1:

    ```julia
    function cmdline_handler(settings::ArgParseSettings, err, err_code::Int = 1)
        println(stderr, err.text)
        println(stderr, usage_string(settings))
        exit(err_code)
    end
    ```

    In interactive mode instead it calls the function `ArgParse.debug_handler`, which just rethrows the error.
  * `exit_after_help` (default = `!isinteractive()`): exit Julia (with error code `0`) when the `:show_help` or `:show_version` actions are triggered. If `false`, those actions will just stop the parsing and make `parse_args` return `nothing`.

Here is a usage example:

```julia
settings = ArgParseSettings(description = "This program does something",
                            commands_are_required = false,
                            version = "1.0",
                            add_version = true)
```

which is also equivalent to:

```julia
settings = ArgParseSettings()
settings.description = "This program does something."
settings.commands_are_required = false
settings.version = "1.0"
settings.add_version = true
```

As a shorthand, the `description` field can be passed without keyword, which makes this equivalent to the above:

```julia
settings = ArgParseSettings("This program does something",
                            commands_are_required = false,
                            version = "1.0",
                            add_version = true)
```

Most settings won't take effect until `parse_args` is invoked, but a few will have immediate effects: `autofix_names`, `error_on_conflict`, `suppress_warnings`, `allow_ambiguous_opts`.
