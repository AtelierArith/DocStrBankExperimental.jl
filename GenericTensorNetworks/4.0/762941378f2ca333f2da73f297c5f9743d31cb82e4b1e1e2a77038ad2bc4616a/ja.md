```
GTNSolver(; optimizer=TreeSA(), single=false, usecuda=false, T=Float64)
```

`ProblemReductions.jl`の`findbest`、`findmin`、および`findmax`インターフェースのための一般的なテンソルネットワークベースのバックエンドです。

## キーワード引数

  * `optimizer`はテンソルネットワーク収束のための最適化手法です。
  * `single`はすべての解の代わりに単一の解を返すスイッチです。
  * `usecuda`はCUDAを使用するためのスイッチです（該当する場合）。このスイッチをオンにする前に、ユーザーは`using CUDA`文を呼び出す必要があります。
  * `T`は「基本」要素タイプであり、時にはメモリコストを削減するために使用できます。
