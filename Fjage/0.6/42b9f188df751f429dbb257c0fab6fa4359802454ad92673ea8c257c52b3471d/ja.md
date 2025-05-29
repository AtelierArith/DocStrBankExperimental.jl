```
send(aid, msg)
```

指定されたエージェントにゲートウェイを介してメッセージを送信します。指定されたエージェントID（`aid`）は、`agent(gw, name)`関数から取得した「所有された」エージェントIDであるか、`agentforservice(gw, service)`関数によって返される必要があります。
