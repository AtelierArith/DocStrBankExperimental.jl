```
function MTKParameters(sys::AbstractSystem, p, u0 = Dict(); t0 = nothing)
```

Create an `MTKParameters` object for the system `sys`. `p` (`u0`) are symbolic maps from parameters (unknowns) to their values. The values can also be symbolic expressions, which are evaluated given the values of other parameters/unknowns. `u0` is only required if the values of parameters depend on the unknowns. `t0` is the initial time, for time- dependent systems. It is only required if the symbolic expressions also use the independent variable of the system.

This requires that `complete` has been called on the system (usually via `structural_simplify` or `@mtkbuild`) and the keyword `split = true` was passed (which is the default behavior).
