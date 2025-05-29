```
abstract type AbstractWorld end
```

注釈付きアクセシビリティグラフ（クリプキ構造）のノードのための抽象型です。これは、例えば、モーダル論理において、式の真偽が*世界*、つまりグラフのノードに相対化される場合に使用されます。

# 実装

新しい世界タイプを実装する際には、論理的意味論を`accessibles`メソッドを通じて定義する必要があります。`accessibles`のヘルプを参照してください。

[`AbstractKripkeStructure`](@ref)や[`AbstractFrame`](@ref)も参照してください。
