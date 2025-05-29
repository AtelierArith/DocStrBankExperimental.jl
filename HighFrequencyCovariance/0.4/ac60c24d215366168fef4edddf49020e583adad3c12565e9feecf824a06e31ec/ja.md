```
valid_correlation_matrix(mat::Hermitian, min_eigen_threshold::Real = 0.0)

valid_correlation_matrix(covar::CovarianceMatrix, min_eigen_threshold::Real = 0.0)
```

`Hermitian` 行列が有効な相関行列であるかどうかをテストします。これは、行列が正定値であるか、対角要素がすべて1であるか、他のすべての要素が1未満であるかをテストすることによって行われます。`Hermitian` が入力された場合は、それがテストされます。`CovarianceMatrix` が入力された場合は、その相関行列がテストされます。

### 入力

  * `mat` - `Hermitian` 行列または `CovarianceMatrix`
  * `min_eigen_threshold` - 最小固有値がどれだけ大きくなければならないか。

### 戻り値

  * `mat` が有効な相関行列であれば true を返し、そうでなければ false を返す `Bool`。
