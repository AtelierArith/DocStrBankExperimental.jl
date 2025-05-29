`coxeter_matrix(p)` は `Poset` または `CPoset` のコクセター行列で、`m` が ζ またはインシデンス行列であるとき、`-m*transpose(inv(m))` と定義されます。

```julia-repl
julia> coxeter_matrix(CPoset(:diamond,5))
5×5 Matrix{Int64}:
  0  0  0  0  -1
 -1  0  1  1  -1
 -1  1  0  1  -1
 -1  1  1  0  -1
 -2  1  1  1  -1
```
