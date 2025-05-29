```
figure(; ...)
```

新しい [`Figure`](@ref) を作成し、それを返します。

受け入れ可能なキーワード引数は次のとおりです：

  * [`Figure`](@ref) によって受け取られるものは何でも。
  * `x_range`/`y_range`: x/y範囲を設定します。要因のベクトルまたは区間を表す2タプルである場合があります。デフォルト: `DataRange1d()`。
  * `x_axis`/`y_axis`: x/y軸を設定します。抑制するために `nothing` を指定できます。デフォルト: `LinearAxis()`。
  * `x_axis_location`/`y_axis_location`: 軸を配置する場所。 `"left"`、`"right"`、`"above"` または `"below"` のいずれか。デフォルト: `"below"`/`"left"`。
  * `x_axis_label`/`y_axis_label`: x/y軸のラベルを設定します。
  * `x_grid`/`y_grid`: x/yグリッドを設定します。抑制するために `nothing` を指定できます。
  * `tools`: ツールバーを作成するためのオプションのツールのリスト。
  * `tooltips`: 指定された場合、これらのツールチップを持つ [`HoverTool`](@ref) を追加します。
