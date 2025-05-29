```
UASP(client, baseport)
UASP(client, baseport, ipaddr)
```

UDPポート`baseport`と`baseport+1`で実行されるUASPデーモンを作成します。IPアドレスが指定されていない場合、デーモンはローカルホストにのみバインドされます。`client`はプロトコルインターフェースメソッドをサポートしている必要があります（詳細は`Node`を参照してください）。
