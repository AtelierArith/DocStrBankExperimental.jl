```
mag, phase, w = bode(sys[, w]; unwrap=true)
```

Compute the magnitude and phase parts of the frequency response of system `sys` at frequencies `w`. See also [`bodeplot`](@ref)

`mag` and `phase` has size `(ny, nu, length(w))`. If `unwrap` is true (default), the function `unwrap!` will be applied to the phase angles. This procedure is costly and can be avoided if the unwrapping is not required.

For higher performance, see the function [`bodemag!`](@ref) that computes the magnitude only.
