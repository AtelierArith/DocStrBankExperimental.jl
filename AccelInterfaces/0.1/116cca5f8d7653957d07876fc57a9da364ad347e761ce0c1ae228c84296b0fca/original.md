```
@jexitdata [name][, clauses...]
```

Dealloc device memory or copy data from device memory.

If `name` is not specified, the currently active accel context will be used.

# Arguments

  * `name`::String: a unique name for the accelerator context
  * `delete`::NTuple:
  * `updatefrom`::NTuple:
  * `async`::Keyword :

See also [`@jaccel`](@jaccel), [`@jkernel`](@jkernel)

# Examples

```julia-repl
julia> @jexitdata myacc delete(X, Y, Z), updatefrom(X, Y, Z)
0
```

# Implementation

T.B.D.
