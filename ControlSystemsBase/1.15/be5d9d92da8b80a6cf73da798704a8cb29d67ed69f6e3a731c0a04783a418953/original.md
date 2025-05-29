```
sv, w = sigma(sys[, w])
```

Compute the singular values `sv` of the frequency response of system `sys` at frequencies `w`. See also [`sigmaplot`](@ref)

`sv` has size `(min(ny, nu), length(w))`
