```
forget(α::Bdd, x::Integer)::Bdd = eliminate(α, x)
forget(α::Bdd, X::Union{Set, BitSet, AbstractVector{T}}) where T <: Integer
```

Returns the resulting BDD after applying the `forget` operation. Equivalent to $\phi|_x \vee \phi|_{\neg x}$.
