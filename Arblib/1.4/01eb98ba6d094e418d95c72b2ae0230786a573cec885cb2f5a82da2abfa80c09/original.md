```
AcbMatrix <: DenseMatrix{Acb}
AcbMatrix(r::Integer, c::Integer; prec::Integer = _current_precision())
AcbMatrix(A::AcbMatrixLike; shallow::Bool = false, prec::Integer = precision(v))
AcbMatrix(A::AbstractMatrix; prec::Integer = _precision(v))
AcbMatrix(v::AbstractVector; prec::Integer = _precision(v))
```

The constructor with `r::Integer, c::Integer` returns a `r × c` filled with zeros. The other three constructors returns a copy of the given matrix or vector. If `shallow = true` then the returned matrix shares the underlying data with the input, mutating one of them mutates both.

See also [`AcbRefMatrix`](@ref).
