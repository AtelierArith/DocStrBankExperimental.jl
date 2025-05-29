```
Arg(name::String, element; required=true, short_name=nothing, type=nothing)
```

Construct a wrapper around a Pluto element that is a CLI option called –<name> if not run from Pluto.

Keyword arguments:

  * `required`: if passing this option is required if running from CLI. If   `required == false` and the option is not passed, the `initial_value`of the    PlutoUI element will be taken.
  * `short_name`: the single-dashed short cli name, if you pass "k" it will be -k
  * `type`: override type to convert the CLI argument into, if `nothing`, the type of   `initial_value` will be considered
  * `args`: CLI args (defaults to `ARGS`)
