```
spawn(service, actor::Actor, [pos::Pos])::Addr
```

指定されたアクターを `service` で表されるスケジューラ上に生成し、そのアドレスを返します。

アクターAPIの一部であり、取得した `service` を提供するライフサイクルコールバックから呼び出すことができます。

`OnSpawn` メッセージは、この関数が返る前に `actor` に配信されます。

# 例

# TODO: このサンプルを更新する

```
mutable struct ListItem{TData, TCore} <: Actor{TCore}
    data::TData
    next::Union{Nothing, Addr}
    core::TCore
    ListItem(data, core) = new{typeof(data), typeof(core)}(data, nothing, core)
end

struct Append{TData}
    value::TData
end

function CircoCore.onmessage(me::ListItem, message::Append, service)
    me.next = spawn(service, ListItem(message.value))
end
```
