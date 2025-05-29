```
refame(name, value)
```

与えられた値を[`FameObject`](@ref)に変換します。

  * `Real` => 数値スカラー（整数を含む）
  * `Float64` => 精度スカラー
  * `Bool` => ブールスカラー
  * [`MIT`](@ref TimeSeriesEcon.MIT) => 日付スカラー
  * `String` => 名前リスト（形式が"{name1,name2,...}"の場合）、それ以外は文字列スカラー
  * `Vector{String}` => 文字列のケースシリーズ
  * [`TSeries`](@ref TimeSeriesEcon.TSeries) => 同じ頻度とタイプのシリーズ。型変換はスカラーの場合と同じです。
