```
@jaccel [name][, clauses...]
```

Create accelerator context.

If `name` is not specified, this context can be accessed only as the currently active context.

# Arguments

  * `name`::String: a unique name for this accelerator context
  * `framework`::NamedTuple:
  * `device`::Integer:
  * `compiler`::Integer:
  * `machine`::Integer:
  * `constant`::Tuple of Variable literal :
  * `set`::Named Tuple:

See also [`@jdecel`](@jdecel), [`@jkernel`](@jkernel)

# Examples

```julia-repl
julia> @jaccel myacc framework(fortran="gfortran -fPIC -shared -g")
AccelInfo
```

# Implementation

T.B.D.
