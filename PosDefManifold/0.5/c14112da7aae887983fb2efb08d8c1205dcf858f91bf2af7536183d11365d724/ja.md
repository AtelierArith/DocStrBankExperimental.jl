```
choInv!(P::AbstractArray{T};
	kind::Symbol = :LLt, tol::Real = √eps(T)) where T<:RealOrComplex
```

[`choInv`](@ref) と同じですが、入力行列を破壊します。この関数は入力行列をコピーする必要がないため、わずかに速くなります。
