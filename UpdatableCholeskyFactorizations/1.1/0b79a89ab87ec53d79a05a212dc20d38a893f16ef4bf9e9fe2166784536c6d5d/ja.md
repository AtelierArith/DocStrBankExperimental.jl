```
updatable_cholesky(A::AbstractMatrix, m::Int = 2size(A, 1); check::Bool = true)
```

`n by n` 行列 `A` から始まる更新可能なコレスキー分解を計算し、行列への将来の追加のために `m x m` 行列を事前に割り当てます（デフォルトはサイズ `2n` の2倍です）。
