```
struct AppendConcatSemiring{T<:Union{Monoid,Semiring}} <: Semiring
    val::Set{T}
end
```

Append-Concatenation semiring: $R = (\Sigma\^*, [x, y], \cdot, \{\}, \{\epsilon\})$ over set of symbol sequence.
