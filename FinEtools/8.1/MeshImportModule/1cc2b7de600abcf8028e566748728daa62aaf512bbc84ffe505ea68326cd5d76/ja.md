```
import_MESH(filename)
```

MESH形式（.mesh、.xyz、.connの3つのファイル）のメッシュをインポートします。

# 出力

データ辞書、キーは次の通りです。

  * "`fens`" = 有限要素ノード。
  * "`fesets`" = 有限要素セットの配列。
