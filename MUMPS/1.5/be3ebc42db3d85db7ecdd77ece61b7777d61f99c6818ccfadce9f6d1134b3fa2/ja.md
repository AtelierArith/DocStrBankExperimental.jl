```
solve(A, rhs; sym=mumps_unsymmetric)
```

初期化 / 分析 / 因数分解 / 解決を組み合わせています。`A` と `rhs` がすべてのノードで利用可能であると仮定します。オプションのキーワード引数 `sym` は `A` の対称性を示します。解は取得され、返されます。
