```
ProgressParams(; progress_token::ProgressToken, progress::Float64,
             total::Union{Float64,Nothing}=nothing) <: RequestParams
```

長時間実行される操作中の進捗通知のためのパラメータ。

# フィールド

  * `progress_token::ProgressToken`: 報告されている操作を識別するトークン
  * `progress::Float64`: 現在の進捗値
  * `total::Union{Float64,Nothing}`: オプションの期待される合計値
