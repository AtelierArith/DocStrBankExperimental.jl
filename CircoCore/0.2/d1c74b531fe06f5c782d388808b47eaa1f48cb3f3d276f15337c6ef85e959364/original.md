```
spawn(service, actor::Actor, [pos::Pos])::Addr
```

Spawn the given actor on the scheduler represented by `service`, return the address of it.

Part of the actor API, can be called from a lifecycle callback, providing the `service` you got.

The `OnSpawn` message will be delivered to `actor` before this function returns.

# Examples

# TODO: update this sample

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
