```
only_in_nb(ex)
```

Executes the expression `ex` only if the macro is called from a running Pluto instance and ran directly from the source notebook file.

This is more strict than `PlutoHooks.@skip_as_script` as including a notebook with `@skip_as_script ex` from another notebook would still execute `ex`.
`@only_in_nb ex` instead only evaluates `ex` if the calling notebook is the original source notebook file.

See also: [`@only_out_nb`](@ref). [`PlutoHooks.@skip_as_script`](@ref).
