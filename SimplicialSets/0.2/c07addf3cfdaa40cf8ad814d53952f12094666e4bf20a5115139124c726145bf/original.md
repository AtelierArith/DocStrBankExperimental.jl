```
SymbolicSimplex{L<:Union{Symbol,Char}} <: AbstractSimplex

SymbolicSimplex(label, w::AbstractVector{<:Integer})
SymbolicSimplex(label, n::Integer)
```

This type represents "symbolic simplices" that are given by a label and a weakly increasing sequence of non-negative integers enumerating the vertices. Such a simplex is degenerate if any integer is repeated.

The label can be of type `Symbol` or `Char`. The vertex numbers must be between `0` and `31`, and the dimension cannot be larger than `24`. If an integer `n` is passed as a second argument to the constructor, then the vertices are `0:n`.
