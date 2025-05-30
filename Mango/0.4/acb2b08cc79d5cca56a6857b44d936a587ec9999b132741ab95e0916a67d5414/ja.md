```
subscribe_send(role::Role, handler::Function)
```

`send_message` フックを関数にサブスクライブします (シグネチャ、(role, content, receiver*id, receiver*addr; kwargs...)) メッセージ送信時に。この関数内のフックは、エージェントによってメッセージが送信されるたびに呼び出されます。
