```
@jwait [kernelname[ accelname]]
```

Wait to finish device operation

If `kernelname` or `accelname` is not specified, the currently active accel or kernel context will be used.

# Arguments

See also [`@jaccel`](@jaccel), [`@jkernel`](@jkernel)

# Examples

```julia-repl
julia> @jwait mykernel
0
```

# Implementation

T.B.D.
