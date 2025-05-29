```
abstract type AbstractLatex <: AbstractRenderType end
```

ほとんどのプレーンテキストレンダリングのための抽象型です。印刷は `AbstractLatex` を使用して定義されているため、異なるデフォルトを持つ新しいテーブルを `AbstractLatex` をサブタイピングすることで最小限の労力で作成できます。
