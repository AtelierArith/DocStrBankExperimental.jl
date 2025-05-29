```
struct AppendConcatSemiring{T<:Union{Monoid,Semiring}} <: Semiring
    val::Set{T}
end
```

Append-Concatenation セミリング: $R = (\Sigma\^*, [x, y], \cdot, \{\}, \{\epsilon\})$ シンボル列の集合上。
