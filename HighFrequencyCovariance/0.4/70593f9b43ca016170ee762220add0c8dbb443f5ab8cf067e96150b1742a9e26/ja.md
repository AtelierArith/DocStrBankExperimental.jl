```
nearest_psd_matrix(mat::Hermitian)
```

この関数は、エルミート行列を最近のpsd行列にマッピングします。これはHigham（2001; 定理3.2）の`project_to_S`メソッドを使用します。この場合、特別な重み付けは適用されません。高度なユーザーは、`closest` pds行列を決定するために重みを使用したい場合、`project_to_S`を直接使用できます。

### 入力

  * `mat` - psd行列にマッピングしたい行列

### 結果

  * `Hermitian`

    nearest*psd*matrix(       covariance*matrix::CovarianceMatrix;       apply*to_covariance::Bool = true,   )

この関数は、エルミート行列を最近のpsd行列にマッピングします。これはHigham（2001; 定理3.2）の`project_to_S`メソッドを使用します。この場合、特別な重み付けは適用されません。高度なユーザーは、`closest` pds行列を決定するために重みを使用したい場合、`project_to_S`を直接使用できます。

### 入力

  * `covariance_matrix` - psd行列にマッピングしたい行列
  * `apply_to_covariance` - 相関行列または共分散行列に正則化を適用すべきか。

### 結果

  * `CovarianceMatrix`

    nearest*psd*matrix(       covariance*matrix::CovarianceMatrix,       ts::SortedDataFrame;       apply*to_covariance::Bool = true,   )

この関数は、エルミート行列を最近のpsd行列にマッピングします。これはHigham（2001; 定理3.2）の`project_to_S`メソッドを使用します。この場合、特別な重み付けは適用されません。高度なユーザーは、`closest` pds行列を決定するために重みを使用したい場合、`project_to_S`を直接使用できます。

### 入力

  * `covariance_matrix` - psd行列にマッピングしたい行列
  * `ts` - Tickデータ
  * `apply_to_covariance` - 相関行列または共分散行列に正則化を適用すべきか。

### 結果

  * `CovarianceMatrix`

### 参考文献

Higham NJ (2002). "Computing the nearest correlation matrix - a problem from finance." IMA Journal of Numerical Analysis, 22, 329–343. doi:10.1002/nla.258.
