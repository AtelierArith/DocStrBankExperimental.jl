```julia
stem(; y, stem_color, stem_thickness, kwargs...)

```

"ステム"または"ロリポップ"トレースを作成します。これは、エラーバーを使用してステムを描画するために、plotly.jsの`scatter`タイプを使用して実装されています。

## キーワード引数:

  * `error_y`を除く`scatter`が受け入れるすべてのプロパティ。これはステムを描画するために使用されます
  * stem_color - ステムの色を設定します
  * stem_thickness - ステムの太さを設定します
