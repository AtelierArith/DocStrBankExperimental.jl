```
ph_reduce!(matrix::SparseMatrix; [returnbasis=true])
```

行列に対して持続的削減アルゴリズムを適用します。

関数は次の値を返します。

  * `phsingles::Vector{Vector{Int}}`
  * `phpairs::Vector{Vector{Tuple{Int,Int}}}`
  * `basis::SparseMatrix`（`returnbasis=true`の場合）

`matrix`が厳密上三角行列であると仮定します。関数は、`phsingles`に無限長持続区間の開始列を返し、`phpairs`に有限長持続区間の出生列と死亡列を返します。オプション引数`returnbasis=true`が指定されている場合、関数は計算された基底行列Bも返し、`reduced = matrix * B`となります。
