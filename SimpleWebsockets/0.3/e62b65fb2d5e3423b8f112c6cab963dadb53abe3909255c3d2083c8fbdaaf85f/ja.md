```
listen(callback::Function, client::SimpleWebsockets.WebsocketClient, event::Symbol)
```

クライアントにイベントコールバックを登録します。コールバックは正確に1つの引数を持つ関数でなければなりません。

有効なイベントは次のとおりです：

  * :connect
  * :connectError

# 例

```julia
listen(client, :connect) do ws
    #...
end
```
