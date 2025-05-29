```
walkernumber(v)
```

Compute the number of walkers in `v`. It is used for updating the shift. Overload this function for modifying population control.

In most cases `walkernumber(v)` is identical to `norm(v, 1)`. For `AbstractDVec`s with complex coefficients it reports the one norm separately for the real and the imaginary part as a `ComplexF64`. See [`Norm1ProjectorPPop`](@ref).
