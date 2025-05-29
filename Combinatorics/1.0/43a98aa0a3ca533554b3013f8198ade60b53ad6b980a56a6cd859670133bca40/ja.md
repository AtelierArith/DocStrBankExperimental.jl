```
multiexponents(m, n)
```

多項式展開 (x₁ + x₂ + ... + xₘ)ⁿ の指数を返します。

例えば、展開 (x₁ + x₂ + x₃)² = x₁² + x₁x₂ + x₁x₃ + ... の指数は次の通りです:

```julia-repl
julia> collect(multiexponents(3, 2))
6-element Vector{Vector{Int64}}:
 [2, 0, 0]
 [1, 1, 0]
 [1, 0, 1]
 [0, 2, 0]
 [0, 1, 1]
 [0, 0, 2]
```
