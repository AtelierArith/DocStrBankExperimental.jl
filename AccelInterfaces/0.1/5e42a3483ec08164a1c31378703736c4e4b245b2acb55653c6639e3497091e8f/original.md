```
@jlaunch [kernelname, [accelname, ]][clauses...]
```

Launch a kernel on an accelerator.

If `kernelname` or `accelname` is not specified, the currently active accel or kernel context will be used.

# Arguments

  * `kernelname`::String: Kernel context name
  * `accelname`::String: Accel context name

See also [`@jaccel`](@jaccel), [`@jkernel`](@jkernel)

# Examples

```julia-repl
julia> @jlaunch mykernel myaccel input(X, Y) output(Z)
0
```

# Implementation

T.B.D.
