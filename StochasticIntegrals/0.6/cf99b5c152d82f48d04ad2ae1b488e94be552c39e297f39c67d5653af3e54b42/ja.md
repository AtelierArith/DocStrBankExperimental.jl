```
get_draws(covar::Union{ForwardCovariance,SimpleCovariance}, num::Integer; number_generator::NumberGenerator = Mersenne(MersenneTwister(1234), length(covar.covariance_labels_)), antithetic_variates = false)
```

`ForwardCovariance` 構造体から擬似乱数を取得します。他のスキーム（準乱数のようなもの）は、均一な*引き出しとして準乱数を挿入することで実行できます。`antithetic*variates` 制御が true に設定されている場合、2 番目の引き出しセットは前のものに対して反対になります。

### 入力

  * `covar` - 引き出しを行いたい `ForwardCovariance` または `SimpleCovariance` 構造体。
  * `num` - 取得したい引き出しの数。
  * `number_generator` - 乱数を生成する方法。
  * `antithetic_variates` - 反対変量サンプリングを希望しますか。

### 戻り値

  * 引き出しの `Dict` の `Vector`。
