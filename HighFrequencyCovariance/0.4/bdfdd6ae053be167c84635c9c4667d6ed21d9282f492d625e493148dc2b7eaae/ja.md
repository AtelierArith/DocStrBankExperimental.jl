```
is_psd_matrix(mat::Hermitian, min_eigen_threshold::Real = 0.0)

is_psd_matrix(covar::CovarianceMatrix)
```

行列がpsd（正半定値）であるかどうかをテストします。これは、すべての固有値が正であるかどうかを確認することによって行われます。`Hermitian`が入力された場合は、それがテストされます。`CovarianceMatrix`が入力された場合は、その相関行列がテストされます。

### 入力

  * `mat` - `Hermitian`行列または`CovarianceMatrix`
  * `min_eigen_threshold` - 最小の固有値がどれくらい大きくなければならないか。

### 戻り値

  * matがpsdであればtrue、そうでなければfalseの`Bool`。
