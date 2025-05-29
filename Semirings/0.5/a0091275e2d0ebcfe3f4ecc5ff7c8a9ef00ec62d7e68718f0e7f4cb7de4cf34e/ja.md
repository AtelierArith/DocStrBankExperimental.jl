```
struct StringSemiring{T<:AbstractString} <: Semiring
    val::T
end
```

文字列半環: $R = (\Sigma\^*, \land, \cdot, \infty, \epsilon)$、ここで $x \land y$ は $x$ と $y$ の最長共通接頭辞であり、$\cdot$ は文字列の連結操作です。
