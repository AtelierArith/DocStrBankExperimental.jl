```
proc_ARGS(pp0::Nothing) = (;abort=false, argpairs = emptyargs())
proc_ARGS(pp0::ArgumentParser) → (;abort, argpairs)
```

Reads and parses the arguments provided to the script from the command line. See the flow diagram in the documentation for details.

# Arguments

  * `pp0::Union{Nothing, ArgumentParser}`: ArgumentParser for command line arguments.

# Returned NamedTuple

  * `abort::Bool`
  * `argpairs`: Vector of pairs `argname::Symbol => argvalue::Any`

Function `proc_ARGS` is public, not exported.
