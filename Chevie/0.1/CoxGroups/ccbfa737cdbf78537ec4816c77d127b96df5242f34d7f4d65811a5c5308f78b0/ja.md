`coxeter_matrix(W)` または `coxmat`

Coxeter群 `W` のCoxeter行列を返します。これは、行列 `m` であり、エントリ `m[i,j]` には `W(i)*W(j)` の順序が含まれています。ここで `W(i)` は `W` の `i` 番目のCoxeter生成子です。無限の順序はエントリ `0` で表されます。

```julia-repl
julia> W=coxsym(4)
𝔖 ₄

julia> coxmat(W)
3×3 Matrix{Int64}:
 1  3  2
 3  1  3
 2  3  1
```
