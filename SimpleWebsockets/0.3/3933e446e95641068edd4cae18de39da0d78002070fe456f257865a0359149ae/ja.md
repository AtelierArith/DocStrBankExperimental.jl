```
listen(callback::Function, server::WebsocketServer, event::Symbol)
```

サーバーにイベントコールバックを登録します。コールバックは正確に1つの引数を持つ関数でなければなりません。

有効なイベントは次のとおりです：

  * :listening
  * :client
  * :connectError
  * :peerError
  * :closed

# 例

```julia
listen(server, :client) do client
    #...
end
```
