```
Subscribe(eventtype::Type, subscriber::Union{Actor, Addr}, filter::Union{Nothing, String, Function} = nothing)
```

指定された `eventtype` のイベントにサブスクライブするためのメッセージです。

サブスクリプションは、トピック文字列または述語関数によってオプションでフィルタリングできます。フィルタリングとサブスクリプション管理は、別のアクターであるイベントディスパッチャによって行われます。

`eventtype` は具体的でなければなりません。

# 例

```julia
    fs = getname(service, "fs")
    send(service, me, fs, Subscribe(FSEvent, me, "MODIFY"))
    send(service, me, fs, Subscribe(FSEvent, me, event -> event.path == "test.txt"))
```
