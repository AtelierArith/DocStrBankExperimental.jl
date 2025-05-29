```
RunReport(args...; kwargs...) -> Manager
```

異なる入力サイズに対するランタイムとメモリ消費のプロファイルを作成します。

# 引数

  * `funcarray::Array{Base.Callable}` または `func::Base.Callable`: プロファイルを取得する関数
  * `genfunc::Base.Callable`: 関数に対して異なるサイズの入力を生成する関数
  * `insizes`: `genfunc` の入力として使用される整数のイテラブル

# キーワード

  * `seconds::Number`: `@benchmarkable` のパラメータ
  * `samples::Integer`: `@benchmarkable` のパラメータ
