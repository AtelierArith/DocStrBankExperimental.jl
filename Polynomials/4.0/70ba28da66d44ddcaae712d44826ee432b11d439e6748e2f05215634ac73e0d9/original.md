```
roots(::AbstractPolynomial; kwargs...)
```

Returns the roots, or zeros, of the given polynomial.

For non-factored, standard basis polynomials the roots are calculated via the eigenvalues of the companion matrix. The `kwargs` are passed to the `LinearAlgebra.eigvals` call.

!!! note
    The default `roots` implementation is for polynomials in the standard basis. The companion matrix approach is reasonably fast and accurate for modest-size polynomials. However, other packages in the `Julia` ecosystem may be of interest and are mentioned in the documentation.

