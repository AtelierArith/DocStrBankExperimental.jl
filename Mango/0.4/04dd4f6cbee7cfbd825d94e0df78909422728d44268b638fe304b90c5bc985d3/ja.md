```
subscribe_message(role::Role, handler::Function, condition::Function)
```

メッセージディスパッチにメッセージハンドラ関数を登録します（この関数は (role, message, meta) のシグネチャを持つ必要があります）。このハンドラ関数は、メッセージが役割のエージェントに到着したときに、指定された条件関数 ((message, meta) -> boolean) が true に評価されるたびに呼び出されます。
