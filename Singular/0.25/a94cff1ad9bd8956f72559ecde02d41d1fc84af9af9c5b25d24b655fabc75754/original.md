```
lift(M::sideal{T}, SM::sideal{T}) where T
```

Represents the generators of `SM` in terms of the generators of `M`. If `SM` is in `M`, `rest` is the null module, otherwise `rest = reduce(SM, std(M))`. Returns `(result, rest)` with for global orderings:     `Matrix(SM) - Matrix(rest) = Matrix(M)*Matrix(result)` for non-global orderings:     `Matrix(SM)*U - Matrix(rest) = Matrix(M)*Matrix(result)` where `U` is some diagonal matrix of units. To compute this `U`, see `lift(M::sideal, SM::sideal, goodShape::Bool, isSB::Bool, divide::Bool)`.
