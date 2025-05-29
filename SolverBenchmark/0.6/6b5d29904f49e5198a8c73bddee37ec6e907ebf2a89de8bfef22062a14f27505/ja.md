```
save_stats(stats, filename; kwargs...)
```

ベンチマーク統計 `stats` を `filename` という名前のファイルに書き込みます。

#### 引数

  * `stats::Dict{Symbol,DataFrame}`: `bmark_solvers` によって返されるベンチマーク統計
  * `filename::AbstractString`: 出力ファイル名。

#### キーワード引数

  * `force::Bool=false`: 既に存在する場合に `filename` を上書きするかどうか
  * `key::String="stats"`: 後で `filename` からデータを読み取るためのキー。

#### 戻り値

このメソッドは、`filename` が存在し、`force==false` の場合にエラーを返します。成功した場合、`jldopen(filename, "w")` の値を返します。
