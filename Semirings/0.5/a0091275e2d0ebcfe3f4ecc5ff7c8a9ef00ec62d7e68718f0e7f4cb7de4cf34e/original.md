```
struct StringSemiring{T<:AbstractString} <: Semiring
    val::T
end
```

String semiring: $R = (\Sigma\^*, \land, \cdot, \infty, \epsilon)$, where $x \land y$ is the longest common prefix between $x$ and $y$, $\cdot$ is the string concatentation operation.
