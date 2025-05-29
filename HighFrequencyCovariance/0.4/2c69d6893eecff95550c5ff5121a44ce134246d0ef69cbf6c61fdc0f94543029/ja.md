```
StochasticIntegrals.ItoSet(covariance_matrix::CovarianceMatrix{<:Real})
```

`CovarianceMatrix`をStochasticIntegralsパッケージの`ItoSet`に変換します。このパッケージは、共分散行列に対応する多変量ガウス分布からのサンプルを生成するなどの操作に使用できます。

### 入力

  * `covariance_matrix` - `StochasticIntegrals.ItoSet`に変換したい`CovarianceMatrix`

### 返り値

  * `StochasticIntegrals.ItoSet`構造体。

### 例

```
using Dates
covar = CovarianceMatrix(make_random_psd_matrix_from_wishart(5), rand(5), [:A,:B,:C,:D,:E], Dates.Hour(1))
iset = ItoSet(covar)
# これがどのように有用なものに使用されるかを見るには、get_draws関数を参照してください。
```
