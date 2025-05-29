```
ページ
```

ブラウザのページ/タブとそれに関連するWebSocketクライアントを表します。

# フィールド

  * `client::WSClient`: 通信のためのWebSocketクライアント
  * `target_id::String`: このページ/タブの一意の識別子
  * `extras::Dict{String, Any}`: 必要に応じて更新される追加のページメタデータ。古くなっている可能性があるため、`update_page!`を実行して更新してください。
