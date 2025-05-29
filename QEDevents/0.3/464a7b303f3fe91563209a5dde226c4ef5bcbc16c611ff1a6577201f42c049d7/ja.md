```
weight(d::ParticleSampleable, sample)
```

与えられた分布に従って、指定されたサンプルの重みを返します。

この関数は、自動的に入力検証と後処理をそれぞれのインターフェース関数を使用して実行します。呼び出しの順序は次のとおりです。

  * [`_assert_valid_input_type`](@ref)
  * [`_assert_valid_input`](@ref)
  * [`_weight`](@ref)
  * [`_post_processing`](@ref)
