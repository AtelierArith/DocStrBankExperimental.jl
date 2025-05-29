```
StochasticIntegrals.get_draws(
    covariance_matrix::CovarianceMatrix{<:Real},
    num::Integer;
    number_generator::NumberGenerator = Mersenne(
        MersenneTwister(1234),
        length(covariance_matrix.labels),
    ),
    antithetic_variates = false,
)
```

`CovarianceMatrix` 構造体から擬似乱数を取得します。これは基本的に、必要な構造体の構築を行う StochasticIntegrals.get*draws の便利なラッパーです。`antithetic*variates` 制御が true に設定されている場合、毎回の描画の2番目のセットは前のセットに対して反対のものになります。Sobol サンプリングのようなことを行いたい場合は、number_generator を変更できます。利用可能なものを確認するには StochasticIntegrals を参照してください（新しいものを作成してプルリクエストを送ることも自由です）。

### 入力

  * `covar` - 描画したい `CovarianceMatrix` 構造体。
  * `num` - 取得したい描画の数。
  * `number_generator` - 一連の単位区間ベクトルを照会できる `NumberGenerator` 構造体で、これが共分散行列によって描画に変換されます。
  * `antithetic_variates` - 反対の変数を使用するかどうかを示すブール値（毎回の描画の2番目は前の描画の1 - uniformdraw から作成されます）。

### 戻り値

  * 描画の `Dict` の `Vector`。これを `StochasticIntegrals.to_dataframe` または `StochasticIntegrals.to_array` を使用してデータフレームまたは配列に変換できます。
