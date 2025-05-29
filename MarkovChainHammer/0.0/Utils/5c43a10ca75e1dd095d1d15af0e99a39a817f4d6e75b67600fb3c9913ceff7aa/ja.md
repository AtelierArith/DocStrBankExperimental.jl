```
histogram(array; bins=minimum([100, length(array)]), normalization=:uniform, custom_range=false)
```

# 説明

```
配列のヒストグラムを計算します。GLMakieでの棒グラフに便利です。
```

# 引数

  * `array::AbstractArray`: ヒストグラムを計算する配列。

# キーワード引数

  * `bins::Integer`: 使用するビンの数。
  * `normalization::AbstractArray`: 使用する正規化。`:uniform`の場合、正規化は均一です。
  * `custom_range::Tuple`: 使用するカスタム範囲。`false`の場合、範囲はデータから計算されます。

# 戻り値

  * `Tuple{AbstractArray, AbstractArray}`: ビンの中心とヒストグラムの値のタプル。
