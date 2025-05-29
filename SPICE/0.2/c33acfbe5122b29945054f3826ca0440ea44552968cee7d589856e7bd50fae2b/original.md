```
uddf(udfunc, x, dx)
```

Routine to calculate the first derivative of a caller-specified function using a three-point estimation.

### Arguments

  * `udfunc`: A callable that computes the scalar value of interest,   e.g. `f(x::Float64) -> Float64`
  * `x`: Independent variable of `udfunc`
  * `dx`: Interval from `x` for derivative calculation

### Output

Returns the approximate derivative of `udfunc` at `x`.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/uddf_c.html)
