```
abstract type AbstractHtml <: AbstractRenderType end
```

ほとんどのプレーンテキストレンダリングのための抽象型。印刷は `AbstractHtml` を使用して定義されているため、異なるデフォルトを持つ新しいテーブルを `AbstractHtml` をサブタイプ化することで最小限の労力で作成できます。
