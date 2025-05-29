```
MultiVector(::CliffordAlgebra, v::NTuple{N,T}) where {N,T<:Real}
MultiVector(::Type{<:CliffordAlgebra}, v::NTuple{N,T}) where {N,T<:Real}
```

Creates a MultiVector by converting the provided vector v to a 1-vector. The internal storage type of the MultiVector is T.
