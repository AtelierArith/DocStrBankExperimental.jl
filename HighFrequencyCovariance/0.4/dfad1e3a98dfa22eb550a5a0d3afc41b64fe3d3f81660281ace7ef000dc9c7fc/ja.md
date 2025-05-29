```
get_correlation(covar::CovarianceMatrix, asset1::Symbol, asset2::Symbol)
```

CovarianceMatrixに格納された2つの資産間の相関を抽出します。

### 入力

  * `covar` - `CovarianceMatrix`
  * `asset1` - 資産を表す`Symbol`。
  * `asset2` - 資産を表す`Symbol`。

### 戻り値

  * スカラー（相関係数）。
