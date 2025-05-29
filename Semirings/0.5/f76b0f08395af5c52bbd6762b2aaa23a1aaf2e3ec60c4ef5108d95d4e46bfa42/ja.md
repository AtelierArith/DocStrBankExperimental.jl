```
struct UnionConcatSemiring{T<:Union{Monoid,Semiring}} <: Semiring
    val::Set{T}
end
```

和結合連結半環: $R = (\Sigma\^*, \cup, \cdot, \{\}, \{\epsilon\})$ シンボル列の集合上。
