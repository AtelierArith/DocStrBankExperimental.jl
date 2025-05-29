```
deriv!(t::TPS{T}, t1::TPS{T}, monomialindex) where {T} -> t 
∂!(t::TPS{T}, t1::TPS{T}, monomialindex)     where {T} -> t
```

Differentiates `t1` wrt the variable/parameter specified by the variable/parameter index, or  alternatively any monomial specified by indexing-by-order OR indexing-by-sparse monomial, and  sets `t` equal to the result in-place. See the `deriv` documentation for examples.
