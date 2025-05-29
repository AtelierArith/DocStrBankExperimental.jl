```
result = nmfmerge(X, ncomponents; tol_final=1e-4, tol_intermediate=sqrt(tol_final), W0=nothing, H0=nothing, kwargs...)
```

データ行列 `X` に対して「NMF-Merge」を実行します。

引数:

  * `X::AbstractMatrix`: 因数分解されるデータ行列
  * `ncomponents::Pair{Int,Int}`: `n1 => n2` の形式で、`n1` コンポーネントから `n2` コンポーネントにマージします。ここで `n1` は過剰成分 NMF のコンポーネント数、`n2` は最終 NMF のコンポーネント数です。`n1 >= n2` が必要です。

また、`ncomponents` は最終的なコンポーネント数を示す整数でも構いません。この場合、`nmfmerge` はマージ前に約 20% のコンポーネントの余剰をデフォルトで使用します。

キーワード引数:

  * `tol_final`: 最終 NMF の許容誤差
  * `tol_intermediate`: 初期および過剰成分 NMF の許容誤差

`W0`, `H0`: 初期 NMF の初期化。`W0` と `H0` のいずれかが `nothing` の場合、初期化には NNDSVD が使用されます。

他のキーワード引数は `NMF.nnmf` に渡されます。
