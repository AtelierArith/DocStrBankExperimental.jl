```
apply!(b::Basis, nelem, tmode::TransposeMode, emode::EvalMode, u::AbstractCeedVector, v::AbstractCeedVector)
```

Apply basis evaluation from nodes to quadrature points or vice versa, storing the result in the [`CeedVector`](@ref) `v`.

`nelem` specifies the number of elements to apply the basis evaluation to; the backend will specify the ordering in CeedElemRestrictionCreateBlocked()

Set `tmode` to `CEED_NOTRANSPOSE` to evaluate from nodes to quadrature or to `CEED_TRANSPOSE` to apply the transpose, mapping from quadrature points to nodes.

Set the [`EvalMode`](@ref) `emode` to:

  * `CEED_EVAL_NONE` to use values directly,
  * `CEED_EVAL_INTERP` to use interpolated values,
  * `CEED_EVAL_GRAD` to use gradients,
  * `CEED_EVAL_WEIGHT` to use quadrature weights.
