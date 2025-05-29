```
@jkernel kerneldef, [kernelname, [accelname, ]][clauses...]
```

Create kernel context.

If `kernelname` or `accelname` is not specified, the currently active accel or kernel context will be used.

# Arguments

  * `kerneldef`::String: Jai kernel definition
  * `kernelname`::String: Kernel context name
  * `accelname`::String: Accel context name

See also [`@jaccel`](@jaccel), [`@jenterdata`](@jenterdata)

# Examples

```julia-repl
julia> @jkernel knlfilepath mykernel myaccel
0
```

# Implementation

T.B.D.
