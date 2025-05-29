```
AcbVector <: DenseVector{Acb}
AcbVector(n::Integer; prec::Integer = _current_precision())
AcbVector(v::AcbVectorLike; shallow::Bool = false, prec::Integer = precision(v))
AcbVector(v::AbstractVector; prec::Integer = _precision(v))
```

The constructor with `n::Integer` returns a vector with `n` elements filled with zeros. The other two constructors returns a copy of the given vector. If `shallow = true` then the returned vector shares the underlying data with the input, mutating one of them mutates both.

See also [`AcbRefVector`](@ref).
