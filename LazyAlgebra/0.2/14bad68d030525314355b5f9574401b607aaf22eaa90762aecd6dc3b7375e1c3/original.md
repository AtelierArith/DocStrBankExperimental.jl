```
vdot([T,] [w,] x, y)
```

yields the inner product of `x` and `y`; that is, the sum of `conj(x[i])*y[i]` or, if `w` is specified, the sum of `w[i]*conj(x[i])*y[i]` (`w` must have real-valued elements), for all indices `i`.  Optional argument `T` is the floating point type of the result.

Another possibility is:

```
vdot([T,] sel, x, y)
```

with `sel` a selection of indices to restrict the computation of the inner product to some selected elements.  This yields the sum of `x[i]*y[i]` for all `i ∈ sel`.

If the arguments have complex-valued elements and `T` is specified as a floating-point type, complexes are considered as vectors of pairs of reals and the result is:

```
vdot(T::Type{AbstractFloat}, x, y)
-> ((x[1].re*y[1].re + x[1].im*y[1].im) +
    (x[2].re*y[2].re + x[2].im*y[2].im) + ...)
```
