```
field(A, indices)
field(A, fieldname)
```

Return an array view of the field of CellArray `A` designated with `indices` or `fieldname` (modifying the view will modify `A`). The view's dimensionality and size are equal to `A`'s. The operation is not supported if parameter `B` of `A` is neither `0` nor `1`.

## Arguments

  * `indices::Int|NTuple{N,Int}`: the `indices` that designate the field in accordance with `A`'s cell type (flat indexing is supported for multi dimensional cells).
  * `fieldname::Symbol`: the `fieldname` that designates the field in accordance with `A`'s cell type.
