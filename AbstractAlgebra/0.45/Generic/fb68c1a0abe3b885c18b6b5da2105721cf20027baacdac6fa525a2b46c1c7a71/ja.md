```
partitionseq(lambda::Partition)
```

`lambda`から構築された`false`と`true`のシーケンス（`BitVector`として）を返します：`lambda`に関連付けられたYoung Diagramの下部輪郭を左から右にトレースし、水平ステップごとに`true`を挿入し、垂直ステップごとに`false`を挿入します。このシーケンスは常に`true`で始まり、`false`で終わります。
