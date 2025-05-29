```
transposer(matrix::AbstractMatrix)::AbstractMatrix
transposer(matrix::NamedMatrix)::NamedMatrix
```

This is a shorthand for `LinearAlgebra.transpose!(similar(transpose(m)), m)`. That is, this will return a transpose of a matrix, but instead of simply using a zero-copy wrapper, it actually rearranges the data. See [`relayout!`](@ref).
