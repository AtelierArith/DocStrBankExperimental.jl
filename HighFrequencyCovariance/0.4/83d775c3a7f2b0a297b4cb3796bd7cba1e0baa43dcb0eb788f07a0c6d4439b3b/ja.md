```
eigenvalue_clean(
    eigenvalues::Vector{<:Real},
    eigenvectors::Matrix{<:Real},
    eigenvalue_threshold::Real,
)
```

これは小さな固有値（値がeigenvalue*threshold未満のもの）を取得します。それらを平均値またはeigenvalue*threshold/(4*number*of*small_eigens)の大きい方に設定します。次に、行列が再構築され、返されます（`Hermitian`として）。

### 入力

  * `eigenvalues` - 行列の固有値。
  * `eigenvectors` - 行列の固有ベクトル。
  * `eigenvalue_threshold` - 固有値を変更するための閾値。

### 戻り値

  * `Hermitian`。

    eigenvalue*clean(mat::Hermitian, eigenvalue*threshold::Real)

これは行列をその固有値と固有ベクトルに分割します。次に、小さな固有値（値が`eigenvalue_threshold`未満のもの）を取得します。それらを平均値または`eigenvalue_threshold/(4*number_of_small_eigens)`の大きい方に設定します。次に、行列が再構築され、返されます（`Hermitian`として）。

### 入力

  * `mat` - 固有値正則化で正則化したい行列。
  * `eigenvalue_threshold` - 固有値を変更するための閾値。

### 戻り値

  * `Hermitian`。

    eigenvalue_clean(mat::Hermitian, ts::SortedDataFrame)

上記の2つのメソッドと同様に、これらの関数は小さな固有値をほぼゼロに設定することによって行列を正則化します。閾値を選択するためにLaloux、Cizeau、Bouchaud & Potters 2000の手法が使用されます。

### 入力

  * `mat` - 固有値正則化で正則化したい行列。
  * `ts` - ティックデータ。

### 戻り値

  * `Hermitian`。

    eigenvalue*clean(       covariance*matrix::CovarianceMatrix,       ts::SortedDataFrame;       apply*to*covariance::Bool = true,   )

### 入力

  * `mat` - 固有値正則化で正則化したい行列。
  * `ts` - ティックデータ。
  * `apply_to_covariance` - 正則化を共分散行列に適用するか相関行列に適用するか。

### 戻り値

  * `CovarianceMatrix`。

入力行列にNaN項が含まれている場合、正則化は不可能であることに注意してください。行列は静かに返されます（これらのNaNは一般的に上流の問題から来るため、この時点でエラーを投げるのではなく行列を返すことが有用です）。その結果、出力は確認する必要があります。

## 参考文献

Laloux, L., Cizeau, P., Bouchaud J. , Potters, M. 2000. "Random matrix theory and financial correlations" International Journal of Theoretical Applied FInance, 3, 391-397.
