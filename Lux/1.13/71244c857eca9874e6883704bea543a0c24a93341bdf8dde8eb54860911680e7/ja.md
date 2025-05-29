```
AlphaDropout(p::Real)
```

AlphaDropoutレイヤー。

## 引数

  * `p`: ドロップアウトの確率

      * `p = 0` の場合、[`NoOpLayer`](@ref) が返されます。
      * `p = 1` の場合、`WrappedLayer(Base.Fix1(broadcast, zero))` が返されます。

## 入力

  * `x`: AbstractArrayである必要があります。

## 戻り値

  * `training=Val(true)` の場合はドロップアウトマスクが適用された `x`、それ以外の場合は単に `x` が返されます。
  * 更新された `rng` を持つ状態。

## 状態

  * `rng`: 擬似乱数生成器
  * `training`: トレーニング/推論モードを確認するために使用されます。

[`Lux.testmode`](@ref) を呼び出してテストモードに切り替えます。

[`Dropout`](@ref)、[`VariationalHiddenDropout`](@ref) も参照してください。
