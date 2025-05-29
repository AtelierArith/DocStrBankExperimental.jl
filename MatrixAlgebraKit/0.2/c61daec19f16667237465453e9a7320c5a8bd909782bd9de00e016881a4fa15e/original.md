```
MatrixAlgebraKit.findtruncated_sorted(values::AbstractVector, strategy::TruncationStrategy)
```

Like [`MatrixAlgebraKit.findtruncated`](@ref) but assumes that the values are sorted in reverse order by absolute value. However, note that this assumption is not checked, so passing values that are not sorted in that way can silently give unexpected results. This is used in the default implementation of [`svd_trunc!`](@ref).
