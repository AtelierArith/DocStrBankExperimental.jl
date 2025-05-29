```
real(p::AbstractPolynomial)
```

Construct a real polynomial from the real parts of the coefficients of `p`.

See also: [`isreal`](@ref)

!!! note
    This could cause losing terms in `p`. This method is usually called on polynomials like `p = Polynomial([1, 2 + 0im, 3.0, 4.0 + 0.0im])` where you want to chop the imaginary parts of the coefficients of `p`.

