```
function evaluate_mps(
    mps::Union{ITensorMPS.MPS,ITensorMPS.MPO},
    indices::AbstractVector{<:ITensorMPS.Index},
    indexvalues::AbstractVector{Int}
)
```

Evaluates an MPS or MPO for a given set of index values.

  * `indices` is a list of `ITensorMPS.Index` objects that specifies the order in which indices are given.
  * `indexvalues` is a list of integer values in the same order as `indices`.

If many evaluations are necessary, it may be advantageous to convert your MPS to a `TensorCrossInterpolation.TTCache` object first.
