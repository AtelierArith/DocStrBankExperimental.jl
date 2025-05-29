```
re, im, w = nyquist(sys[, w])
```

Compute the real and imaginary parts of the frequency response of system `sys` at frequencies `w`. See also [`nyquistplot`](@ref)

`re` and `im` has size `(ny, nu, length(w))`
