```
順列
```

  * `Permutation(list)` は新しい `Permutation` を作成します。ここで `list` は `1:n` の再配置でなければなりません。
  * `Permutation(n)` は `1:n` の恒等 `Permutation` を作成します。
  * `Permutation(n,k)` は `1:n` の `k` 番目の `Permutation` を作成します。
  * `Permutation(P::Matrix{Int})` は順列行列から `Permutation` を作成します。
  * `Permutation(cycles::Vector{Vector{Int}})` は不連結サイクルのリストから `Permutation` を作成します。
