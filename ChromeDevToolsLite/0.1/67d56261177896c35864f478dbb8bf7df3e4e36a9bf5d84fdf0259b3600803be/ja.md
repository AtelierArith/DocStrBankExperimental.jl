```
press_key(client::WSClient, key::String; modifiers::Vector{String} = String[],
    verbose::Bool = false)
```

キーボードのキーを押して離します。

# 引数

  * `client::WSClient`: アクションを実行するWebSocketクライアント
  * `key::String`: 押すキー（例："a", "Enter", "ArrowUp"）
  * `modifiers::Vector{String}=String[]`: キーボード修飾キー（例：["Shift", "Control"]）
  * `verbose::Bool=false`: 詳細な出力を表示するかどうか
