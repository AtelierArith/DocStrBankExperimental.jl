```
get_element_position(ws_client::WSClient, element_handle::String)
```

ページ上の要素の位置を取得します。

# 引数

  * `ws_client::WSClient`: WebSocketクライアント接続
  * `element_handle::String`: 対象要素のCSSセレクタ

# 戻り値

要素の中心のxおよびy座標を含むNamedTuple
