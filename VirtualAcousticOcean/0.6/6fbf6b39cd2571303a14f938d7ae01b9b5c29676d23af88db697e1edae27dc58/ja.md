```
UASP2(client, port)
UASP2(client, port, ipaddr)
```

TCP `port` で実行する UASP v2 デーモンを作成します。IP アドレスが指定されていない場合、デーモンはローカルホストにのみバインドされます。`client` はプロトコルインターフェースメソッドをサポートしている必要があります（詳細は `Node` を参照してください）。
