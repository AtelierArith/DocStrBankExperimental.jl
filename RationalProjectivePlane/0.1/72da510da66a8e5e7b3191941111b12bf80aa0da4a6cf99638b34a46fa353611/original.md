```
transform(a::PP, b::PP, c::PP = PP(0, 0, 1))::Matrix{Rational{Int}}
```

Create a matrix `M` with the property that `M(a)` is `(1 : 0 : 0)`, `M(b)` is `(0 : 1 : 0)`, and `M(c)` is `(0 : 0 : 1)`.
