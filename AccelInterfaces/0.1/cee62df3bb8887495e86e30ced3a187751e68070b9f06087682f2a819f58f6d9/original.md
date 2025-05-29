```
@jdecel [name][, clauses...]
```

Destroy accelerator context.

If `name` is not specified, this context can be accessed only as the currently active context.

# Arguments

  * `name`::String: a unique name for this accelerator context

See also [`@jaccel`](@jaccel), [`@jkernel`](@jkernel)

# Examples

```julia-repl
julia> @jdecel myacc
```

# Implementation

T.B.D.
