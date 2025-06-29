```
fit(PPCA, X; ...)
```

与えられた行列 `X` のデータに対して確率的PCAを実行します。`X` の各列は観測値です。このメソッドは [`PPCA`](@ref) のインスタンスを返します。

**キーワード引数:**

`(d, n) = size(X)` をそれぞれ入力次元と観測数とします：

  * `method`: メソッドの選択：

      * `:ml`: 確率的PCAの最大尤度版を使用 (*デフォルト*)
      * `:em`: 確率的PCAのEM版を使用
      * `:bayes`: ベイズPCAを使用
  * `maxoutdim`: 最大出力次元 (*デフォルト* `d-1`)
  * `mean`: 平均ベクトルで、次のいずれかです：

      * `0`: 入力データはすでに中心化されています
      * `nothing`: この関数は平均を計算します (*デフォルト*)
      * 事前に計算された平均ベクトル
  * `tol`: 収束許容誤差 (*デフォルト* `1.0e-6`)
  * `maxiter`: 最大反復回数 (*デフォルト* `1000`)

**注意:** この関数は、選択したメソッドに応じて内部的に [`ppcaml`](@ref)、[`ppcaem`](@ref) または [`bayespca`](@ref) を呼び出します。
