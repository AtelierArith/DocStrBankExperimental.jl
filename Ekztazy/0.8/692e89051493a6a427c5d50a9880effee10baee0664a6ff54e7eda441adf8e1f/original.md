```
extops(ops::Vector)
```

Creates a Dict of `option name` -> `option value` for the given vector of [`ApplicationCommandOption`](@ref).  If the option is of `Subcommand` type, creates a dict for all its subcommands.
