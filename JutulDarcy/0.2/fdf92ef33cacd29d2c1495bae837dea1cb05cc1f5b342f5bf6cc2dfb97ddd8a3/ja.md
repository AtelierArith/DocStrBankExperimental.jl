```
coarsen_reservoir_case(case, coarsedim; kwargs...)
```

指定された次元に対して与えられた貯水池ケースを粗くします。

# 引数

  * `case`: 粗くする貯水池ケース。
  * `coarsedim`: 粗くされた貯水池の目標次元。

# キーワード引数

  * `method`: パーティショニングに使用する方法。デフォルトは `missing`。
  * `partitioner_arg`: パーティショナーに渡される引数の名前付きタプル。
  * `setup_arg`: `coarsen_reservoir_model` に渡される引数の名前付きタプル。
  * `state_arg`: 状態粗化関数に渡される引数の名前付きタプル。

# 戻り値

  * 粗くされた貯水池ケースのバージョン。
