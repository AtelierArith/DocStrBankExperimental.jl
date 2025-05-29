```
ArbVector <: DenseVector{Arb}
ArbVector(n::Integer; prec::Integer = _current_precision())
ArbVector(v::ArbVectorLike; shallow::Bool = false, prec::Integer = precision(v))
ArbVector(v::AbstractVector; prec::Integer = _precision(v))
```

The constructor with `n::Integer` returns a vector with `n` elements filled with zeros. The other two constructors returns a copy of the given vector. If `shallow = true` then the returned vector shares the underlying data with the input, mutating one of them mutates both.

See also [`ArbRefVector`](@ref).
