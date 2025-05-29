```
prompt_and_parse(pp::Nothing) = (;abort=false, argpairs = emptyargs())
prompt_and_parse(pp::ArgumentParser) → (;abort, argpairs)
```

Prints a prompt, read and parses the input from the user. See the flow diagram in the documentation for details.

# Arguments

  * `pp::Union{Nothing, ArgumentParser}`: ArgumentParser for command line arguments.

# Returned NamedTuple

  * `abort::Bool`
  * `argpairs`: Vector of pairs `argname::Symbol => argvalue::Any`

Function `prompt_and_parse` is public, not exported.
