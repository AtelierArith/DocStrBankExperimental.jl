```
Hashpipe ステータス構造体
```

ハッシュパイプステータスバッファを表すデータ。

既存のステータスバッファに接続する前に、空のステータス構造体を作成する必要があります。例: '''     instance*id = 0     status = status*t(0,0,0,0)     status*attach(instance*id, Ref(status)) '''
