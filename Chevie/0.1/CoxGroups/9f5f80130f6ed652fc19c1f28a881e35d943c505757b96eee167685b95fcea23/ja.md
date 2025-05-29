`coxeter_hyperoctaedral_group(n)` または `coxhyp(n)`

ハイパーオクタヘドラル群（±1,…,±nのすべての符号付き置換の群）は、生成子 `(1,-1)` と `(i,i+1)(-i,-i-1)` を持つタイプ `Bₙ` のコクセター群です。

```julia-repl
julia> elements(coxhyp(2))
8-element Vector{SPerm{Int8}}:
 ()
 (1,2)
 (1,-1)
 (1,2,-1,-2)
 (1,-2,-1,2)
 (2,-2)
 (1,-2)
 (1,-1)(2,-2)
```
