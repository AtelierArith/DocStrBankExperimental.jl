```
chbder(cp, x2s, x, nderiv)
```

Given the coefficients for the Chebyshev expansion of a polynomial, this returns the value of the polynomial and its first `nderiv` derivatives evaluated at the input `x`.

### Arguments

  * `cp`: Chebyshev polynomial coefficients
  * `x2s`: Transformation parameters of polynomial
  * `x`: Value for which the polynomial is to be evaluated
  * `nderiv`: The number of derivatives to compute

### Output

Returns the derivatives of the polynomial.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/chbder_c.html)
