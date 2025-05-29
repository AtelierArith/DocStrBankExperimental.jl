```
type_text(client::WSClient, text::String; modifiers::Vector{String} = String[],
    verbose::Bool = false)
```

各文字のキーボード入力をシミュレートしてテキストを入力します。

# 引数

  * `client::WSClient`: アクションを実行するWebSocketクライアント
  * `text::String`: 入力するテキスト
  * `modifiers::Vector{String}=String[]`: キーボード修飾子（例: ["Shift", "Control"]）
  * `verbose::Bool=false`: 詳細な出力を表示するかどうか
