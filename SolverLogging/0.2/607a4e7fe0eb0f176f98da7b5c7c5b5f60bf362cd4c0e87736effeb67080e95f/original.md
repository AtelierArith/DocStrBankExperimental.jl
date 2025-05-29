```
setentry(logger, name::String, type; kwargs...)
```

Used to add a new entry/field or modify an existing entry/field in the `logger`.

# Adding a new entry

Specify a unique `name` to add a new entry to the logger. The `type` is used to provide  reasonable formatting defaults and must be included. The keyword arguments control  the behavior/formatting of the field:

  * `fmt` A C-style format string used to control the format of the field
  * `index` Column for the entry in the output. Negative numbers insert from the end.
  * `level` Verbosity level for the entry. A higher level will be printed less often.       Level 0 will always be printed, unless the logger is disabled. Prefer to use        a minimum level of 1.
  * `width` Width of the column. Data is left-aligned to this width.
  * `ccrayon` A [`ConditionalCrayon`](@ref) for conditional formatting.

# Modified an existing entry

This method can also modify an existing entry, if `name` is already a field int the logger. The `type` can be omitted in this case. Simply specify any of the keyword arguments  with the new setting.
