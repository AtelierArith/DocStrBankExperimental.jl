```
send_cdp(
    client::WSClient, method::String, params::Dict = Dict();
    increment_id::Bool = true, timeout::Real = CONNECTION_TIMEOUT)
```

Chrome DevTools Protocolメッセージを送信し、応答を待ちます。

# 引数

  * `client::WSClient`: 使用するWebSocketクライアント
  * `method::String`: 呼び出すCDPメソッド（例: "Page.navigate"）
  * `params::Dict`: CDPメソッドのパラメータ（デフォルト: 空のDict）
  * `increment_id::Bool`: メッセージIDカウンタをインクリメントするかどうか（デフォルト: true）
  * `timeout::Real`: 応答のタイムアウト（秒単位）（デフォルト: CONNECTION_TIMEOUT）

# 戻り値

  * `Dict`: CDP応答メッセージ

# 例外

  * `TimeoutError`: 応答がタイムアウトした場合
