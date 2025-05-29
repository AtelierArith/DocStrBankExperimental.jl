```
boxed_correlationsum(X::AbstractStateSpaceSet, εs, r0 = maximum(εs); kwargs...) → Cs
```

最適化されたアルゴリズムを使用して、各サイズ `ε ∈ εs` の [`correlationsum`](@ref) を推定します。このアルゴリズムは、最初にデータをサイズ `r0` のボックスに分配し、その後、各ボックスと各ボックスの隣接ボックスの相関和を計算します。この方法は、ボックスサイズ `r0` がアトラクタの長さよりもかなり小さい場合、[`correlationsum`](@ref) よりもはるかに高速です。`r0` の良い選択肢は、[`estimate_r0_buenoorovio`](@ref) または [`estimate_r0_theiler`](@ref) です。

```
boxed_correlationsum(X::AbstractStateSpaceSet; kwargs...) → εs, Cs
```

この方法では、`X` の最小点間距離と [`estimate_r0_buenoorovio`](@ref) を使用して、計算に適した `εs` を推定し、それも返されます。

## キーワード引数

  * `q = 2` : 相関和の次数。
  * `P = 2` : プリズム次元。
  * `w = 0` : [ザイラーウィンドウ](@ref)。
  * `show_progress = false` : 計算の進行状況バーを表示するかどうか。
  * `norm = Euclidean()` : 距離ノルム。

## 説明

`C_q(ε)` は、すべての `ε ∈ εs` および各ボックスに対して計算され、その後合計されます。データをボックスに分割する方法は、[Theiler1987](@cite) に従って実装されました。`w` は [ザイラーウィンドウ](@ref) です。`P` はプリズム次元です。`P` がデータの次元と異なる場合、ボックス分配には最初の `P` 次元のみが考慮されます（これをプリズム支援バージョンと呼びます）。デフォルトでは `P` は 2 で、これは [^Bueno2007] によって提案されたバージョンです。`P` の代替は [`prismdim_theiler`](@ref) です。`P = dimension(X)` の場合にのみ、ボックス版が元の [`correlationsum`](@ref) に正確であることが保証されます。他の `P` の場合、残りの次元で距離が小さいために含まれるべき点対がスキップされる可能性がありますが、最初の `P` 次元では距離が大きくなります。
