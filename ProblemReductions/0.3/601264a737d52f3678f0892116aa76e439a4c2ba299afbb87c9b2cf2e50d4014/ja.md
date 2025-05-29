```
is_matching(graph::SimpleGraph, config)
```

`config`が`graph`上の有効なマッチングである場合はtrueを返し、頂点が二重にマッチしている場合はfalseを返します。`config`はブール変数のベクトルであり、`edges(graph)`と一対一の対応があります。
