```
ArbMatrix <: DenseMatrix{Arb}
ArbMatrix(r::Integer, c::Integer; prec::Integer = _current_precision())
ArbMatrix(A::ArbMatrixLike; shallow::Bool = false, prec::Integer = precision(v))
ArbMatrix(A::AbstractMatrix; prec::Integer = _precision(v))
ArbMatrix(v::AbstractVector; prec::Integer = _precision(v))
```

The constructor with `r::Integer, c::Integer` returns a `r × c` filled with zeros. The other three constructors returns a copy of the given matrix or vector. If `shallow = true` then the returned matrix shares the underlying data with the input, mutating one of them mutates both.

See also [`ArbRefMatrix`](@ref).
