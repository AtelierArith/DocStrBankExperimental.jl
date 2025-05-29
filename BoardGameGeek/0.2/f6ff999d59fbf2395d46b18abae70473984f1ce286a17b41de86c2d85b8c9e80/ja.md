```
gamereviews(id::Integer; kwargs...)
```

ゲームのレビューをすべてスクレイプします

# キーワード引数

  * `pagesize::Integer`: ページリクエストごとのレビュー数。デフォルトはAPIの最大100です。
  * `waittime::Real`: ページリクエスト間の待機時間（秒）。デフォルトは`2.0f0`です。
