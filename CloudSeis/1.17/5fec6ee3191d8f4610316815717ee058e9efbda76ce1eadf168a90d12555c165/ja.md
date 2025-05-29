```
cscreate(containers[; optional keyword arguments...])
```

新しいCloudSeisデータセットを作成しますが、対応するハンドルを作成せず、データセットを開くこともありません。`optional keyword arguments`については、`csopen`のヘルプを参照してください。

`containers`は`Container`型または`Vector{<:Container}`型のいずれかです。前者の場合、すべてのエクステントは単一のコンテナに格納され、後者の場合、エクステントは複数のコンテナに分散されます。

"r"および"r+"モードでは、既存のデータセットが複数のコンテナに分散されている場合、プライマリコンテナを提供するだけで済みます。"description.json"オブジェクトは"primary"コンテナにあります。
