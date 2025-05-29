```
MatrixAlgebraKit.findtruncated(values::AbstractVector, strategy::TruncationStrategy)
```

Generic interface for finding truncated values of the spectrum of a decomposition based on the `strategy`. The output should be a collection of indices specifying which values to keep. `MatrixAlgebraKit.findtruncated` is used inside of the default implementation of [`truncate!`](@ref) to perform the truncation. It does not assume that the values are sorted. For a version that assumes the values are reverse sorted by absolute value (which is the standard case for SVD) see [`MatrixAlgebraKit.findtruncated_sorted`](@ref).
