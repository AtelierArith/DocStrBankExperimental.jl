```
choInv!(P::AbstractArray{T};
	kind::Symbol = :LLt, tol::Real = √eps(T)) where T<:RealOrComplex
```

The same thing as [`choInv`](@ref), but destroys the input matrix.  This function does nt require copying the input matrix,  thus it is slightly faster.
