```
function evaluate_mps(
    mps::Union{ITensorMPS.MPS,ITensorMPS.MPO},
    indexspecs::Vararg{AbstractVector{<:Tuple{ITensorMPS.Index,Int}}}
)
```

Evaluates an MPS or MPO for a given set of index values.

  * `indexspec` is a list of tuples, where each tuple contains an `ITensorMPS.Index` object specifying an index, and an `Int` corresponding to the value of the specified index.

If many evaluations are necessary, it may be advantageous to convert your MPS to a `TensorCrossInterpolation.TTCache` object first.
