```
transform(a::PP, b::PP, c::PP = PP(0, 0, 1))::Matrix{Rational{Int}}
```

行列 `M` を作成します。`M(a)` は `(1 : 0 : 0)` であり、`M(b)` は `(0 : 1 : 0)` であり、`M(c)` は `(0 : 0 : 1)` です。
