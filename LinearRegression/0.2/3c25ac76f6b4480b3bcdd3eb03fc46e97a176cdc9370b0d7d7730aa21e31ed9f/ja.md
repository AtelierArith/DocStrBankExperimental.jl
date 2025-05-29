```
linregress(X, y; intercept=true, method=SolveQR())
linregress(X, y, weights; intercept=true, method=SolveQR())
```

（重み付き）線形回帰を行い、`ŷ = X * β` が `‖ŷ - y‖²` を最小化するような係数 β を取得します。デフォルトの場合、これは `X \ y` を解くことに対応します。

`LinearRegressor` を返し、これを [`coef`](@ref) に渡して係数 β を抽出するか、ベクトルまたは行列 `X` を使って単一の点または点のセットで予測するために呼び出すことができます。

現在、`X` が行列である場合、`size(X) == (length(y), num_coefs)`（すなわち、各行が1つの観測の特徴を説明する）であると仮定しています。

## キーワード引数:

  * `intercept` が `true` の場合、バイアス項をモデル化するために `X` に暗黙的に1の列を追加します。
  * `method` は線形回帰システムを解く方法を決定します（[`SolveQR`](@ref) および [`SolveCholesky`](@ref) を参照）。
