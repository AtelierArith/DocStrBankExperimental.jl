```
W, H = gsvdnmf(X::AbstractMatrix, ncomponents::Pair{Int,Int}; tol_final=1e-4, tol_intermediate=1e-4, kwargs...)
```

データ行列 `X` に対して「GSVD-NMF」を実行します。

引数:

  * `X`: 非負データ行列
  * `ncomponents`: `n1 => n2` の形式で、`n1` コンポーネントから `n2` コンポーネントに拡張します。ここで、`n1` は初期 NMF（不完全 NMF）のコンポーネント数で、`n2` は最終 NMF のコンポーネント数です。

また、`ncomponents` は最終 NMF のコンポーネント数を示す整数であることもできます。この場合、`gsvdnmf` は初期 NMF ソリューションのコンポーネントを 1 つ増やすことがデフォルトになります。

キーワード引数:

  * `tol_final`: 最終 NMF の許容誤差、デフォルト: `10^{-4}`
  * `tol_intermediate`: 初期 NMF（不完全 NMF）の許容誤差、デフォルト: tol_final

その他のキーワード引数は `NMF.nnmf` に渡されます。 ```
