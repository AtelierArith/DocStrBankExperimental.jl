```
W, H = gsvdnmf(X::AbstractMatrix, W::AbstractMatrix, H::AbstractMatrix, f;
               n2 = size(first(f), 2),
               tol_nmf=1e-4,
               kwargs...)
```

`W` と `H` を `n2` コンポーネントを持つように拡張し、その後 NMF によって洗練します。

引数:

  * `X`: 非負データ行列
  * `W` と `H`: 初期 NMF 因子分解
  * `n2`: 拡張因子分解におけるコンポーネントの数
  * `f`: `X` の SVD（またはトランケート SVD）

キーワード引数:

  * `tol_nmf`: NMF 洗練ステップの許容誤差、デフォルト: 1e-4

他のキーワード引数は `NMF.nnmf` に渡されます。
