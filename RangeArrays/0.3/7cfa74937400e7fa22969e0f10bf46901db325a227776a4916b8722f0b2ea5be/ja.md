```
RepeatedRangeMatrix(r::AbstractRange{T}, at::AbstractVector{T}) where T
```

RepeatedRangeはRangeMatrixのようなもので、ただし1つの範囲と、その範囲が繰り返されるオフセットのベクトルのみを格納します。現時点では、範囲とオフセットのベクトルは同じ要素型でなければなりません。
