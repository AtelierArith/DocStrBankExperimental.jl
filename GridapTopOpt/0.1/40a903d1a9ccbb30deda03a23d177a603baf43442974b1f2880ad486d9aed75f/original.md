```
struct RepeatingAffineFEStateMap <: AbstractFEStateMap
```

A structure to enable the forward problem and pullback for affine finite element operators `AffineFEOperator` with multiple linear forms but only a single bilinear form.

# Parameters

  * `biform`: `IntegrandWithMeasure` defining the bilinear form.
  * `liform`: A vector of `IntegrandWithMeasure` defining the linear forms.
  * `spaces`: Repeated finite element spaces.
  * `spaces_0`: Original finite element spaces that are being repeated.
  * `plb_caches`: A cache for the pullback operator.
  * `fwd_caches`: A cache for the forward problem.
  * `adj_caches`: A cache for the adjoint problem.
