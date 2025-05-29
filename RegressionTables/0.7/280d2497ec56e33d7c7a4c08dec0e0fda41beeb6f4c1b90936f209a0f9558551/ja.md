```
abstract type AbstractAscii <: AbstractRenderType end
```

ほとんどのプレーンテキストレンダリングのための抽象型です。印刷は `AbstractAscii` を使用して定義されているため、異なるデフォルトを持つ新しいテーブルを `AbstractAscii` をサブタイプ化することで最小限の労力で作成できます。
