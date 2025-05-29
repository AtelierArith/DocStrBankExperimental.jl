```
TensorProductOperator{Dim,T}
```

A tensor product operator is a [`MultidimensionalMatrixDerivativeOperator`](@ref) that is the tensor product of one-dimensional derivative operators.

See also [`tensor_product_operator_2D`](@ref).

References:

  * Sigrun Ortleb (2021) Numerical Methods for Fluid Flow:   High Order SBP Schemes, IMEX Advection-Diffusion Splitting and Positivity Preservation for Production-Destruction-PDEs Habilitation thesis, University of Kassel, [DOI: 10.17170/kobra-202301037274](https://doi.org/10.17170/kobra-202301037274), Chapter 1.2.4.
  * Magnus Svärd, Jan Nordström (2014) Review of summation-by-parts schemes for initial-boundary-value problems Journal of Computational Physics 268, pp. 17-38, [DOI: 10.1016/j.jcp.2014.02.031](https://doi.org/10.1016/j.jcp.2014.02.031).
