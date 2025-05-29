```
@jenterdata [name][, clauses...]
```

Allocate device memory or copy data to device memory.

If `name` is not specified, the currently active accel context will be used.

# Arguments

  * `name`::String: a unique name for the accelerator context
  * `alloc`::NTuple:
  * `updateto`::NTuple:
  * `async`::Keyword :

See also [`@jaccel`](@jaccel), [`@jkernel`](@jkernel)

# Examples

```julia-repl
julia> @jenterdata myacc alloc(X, Y, Z), updateto(X, Y, Z)
0
```

# Implementation

T.B.D.
