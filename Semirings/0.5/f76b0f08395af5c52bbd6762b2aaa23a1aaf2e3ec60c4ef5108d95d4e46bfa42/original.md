```
struct UnionConcatSemiring{T<:Union{Monoid,Semiring}} <: Semiring
    val::Set{T}
end
```

Union-Concatenation semiring: $R = (\Sigma\^*, \cup, \cdot, \{\}, \{\epsilon\})$ over set of symbol sequence.
