```
UA_ServerConfig_setMinimal(config, portNumber, certificate)
```

は、1つのエンドポイントを持つ新しいサーバー設定を作成します。この設定は、指定されたポートにTCPネットワーク層を設定し、サーバーにセキュリティポリシー $SecurityPolicy#None$ を持つ単一のエンドポイントを追加します。サーバー証明書を提供することもできますが、これはオプションです。
