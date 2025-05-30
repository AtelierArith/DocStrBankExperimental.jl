```
subscribe_send(role::Role, handler::Function)
```

`send_message` フックを関数に登録します (シグネチャ、(role, content, receiver*id, receiver*addr; kwargs...))。この関数のフックは、エージェントによってメッセージが送信されるたびに呼び出されます。
