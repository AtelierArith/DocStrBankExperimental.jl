```
listen(callback::Function, ws::SimpleWebsockets.WebsocketConnection, event::Symbol)
```

`WebsocketConnection`にイベントコールバックを登録します。コールバックは正確に1つの引数を持つ関数でなければなりません。

有効なイベントは次のとおりです：

  * :message
  * :pong
  * :error
  * :close

# 例

```julia
listen(ws::WebsocketConnection, :message) do message
    #...
end
```
