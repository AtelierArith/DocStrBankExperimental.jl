```
produce!
```

プロデューサーと提供されたリソースに基づいてバッチを生成します。最大可能バッチが生成されます。使用されたリソースはリソース辞書から削除され、生成されたエンティティは製品辞書に追加されます。

# 戻り値

名前付きタプル {products::Entities, resources::Entities, batches::Int64} であり、

  * products = 生成されたエンティティ
  * resources = 残りのリソース
  * batches = 生成されたバッチの数
