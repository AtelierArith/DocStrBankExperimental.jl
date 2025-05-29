```
gens(A::GroupAlgebra, return_full_basis::Val = Val(false))
  -> Vector{GroupAlgebraElem}
```

`basis(A)`の部分集合を返し、$A$を`base_ring(A)`上の代数として生成します。`return_full_basis`が`Val(true)`に設定されている場合、関数は生成子のモノミアルからなる完全基底を含む`Vector{AbstractAssociativeAlgebraElem}`と、これらのモノミアルがどのように構築されるかに関する情報を含む`Vector{Vector{Tuple{Int, Int}}}`も返します。例えば、関数が`g`、`full_basis`、`v`を返す場合、`full_basis[i] = prod( g[j]^k for (j, k) in v[i] )`となります。
