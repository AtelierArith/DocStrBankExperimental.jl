```
identity_regularisation(mat::Hermitian, identity_weight::Real)
```

相関行列を単位行列と混合することによる正則化。

### 入力

  * `mat` - 正則化される行列。
  * `identity_weight` - 単位行列に与える重み。0と1の間である必要があります。

### 戻り値

  * `Hermitian`。

```
identity_regularisation(mat::Hermitian, asset_returns::DataFrame)
```

Ledoit & Wolf 2003に従った単位行列との混合による相関行列の正則化。

### 入力

  * `mat` - 正則化される行列。
  * `ts` - ティックデータ。

### 戻り値

  * `Hermitian`。

    identity*regularisation(       mat::Hermitian,       ts::SortedDataFrame,       mat*labels::Vector;       spacing::Union{Missing,<:Real} = missing,   )

Ledoit & Wolf 2003に従った単位行列との混合による相関行列の正則化。

### 入力

  * `mat` - 正則化される行列。
  * `ts` - ティックデータ。
  * `mat_labels` - 行列内の各資産のラベル。
  * `spacing` - リターンを推定するために使用する間隔。これは単位行列に与える最適な重みを決定するために使用されます。

### 戻り値

  * `Hermitian`。

    identity*regularisation(       covariance*matrix::CovarianceMatrix,       ts::SortedDataFrame;       spacing::Union{Missing,<:Real} = missing,       apply*to*covariance::Bool = true,   )

Ledoit & Wolf 2003に従った単位行列との混合による相関行列の正則化。

### 入力

  * `covariance_matrix` - 正則化される`CovarianceMatrix`。
  * `ts` - ティックデータ。
  * `spacing` - リターンを推定するために使用する間隔。これは単位行列に与える最適な重みを決定するために使用されます。
  * `apply_to_covariance` - 正則化を共分散行列に適用するか相関行列に適用するか。

### 戻り値

  * `CovarianceMatrix`。

    identity*regularisation(       covariance*matrix::CovarianceMatrix,       identity*weight::Real;       apply*to_covariance = false,   )

相関行列を単位行列と混合することによる正則化。

### 入力

  * `covariance_matrix` - 正則化される`CovarianceMatrix`。
  * `identity_weight` - 単位行列に与える重み。0と1の間である必要があります。
  * `apply_to_covariance` - 正則化を共分散行列に適用するか相関行列に適用するか。

### 戻り値

  * `CovarianceMatrix`。

### 参考文献

Ledoit, O. , Wolf, M. 2003. Improved Estimation of the Covariance Matrix of Stock Returns with an application to portfolio selection. Journal of empirical finance. 10. 603-621.
