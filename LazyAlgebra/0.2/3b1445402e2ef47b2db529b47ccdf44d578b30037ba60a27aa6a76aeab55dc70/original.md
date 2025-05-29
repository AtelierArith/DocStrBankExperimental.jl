```
vupdate!(y, [sel,] α, x) -> y
```

overwrites `y` with `α*x + y` and returns `y`.  The code is optimized for some specific values of the multiplier `α`.  For instance, if `α` is zero, then `y` is left unchanged without using `x`.  Computations are performed at the numerical precision of `promote_eltype(x,y)`.

Optional argument `sel` is a selection of indices to which apply the operation. Note that if an index is repeated, the operation will be performed several times at this location.

See also: [`vscale!`](@ref), [`vcombine!](@ref).
