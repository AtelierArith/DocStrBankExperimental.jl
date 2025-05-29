```
abstract type SyntaxStructure <: Formula end
```

論理式の純粋な構文コンポーネントのための抽象型（例：関連するファンシーなメモ化構造はない）。典型的な表現は[`SyntaxTree`](@ref)ですが、異なる実装は特定の構文形式（例：[結合](https://en.wikipedia.org/wiki/Conjunctive_normal_form)または[選択](https://en.wikipedia.org/wiki/Disjunctive_normal_form)標準形）をカバーできます。

# インターフェース

  * [`Formula`](@ref)も参照してください

[`Formula`](@ref)、[`AbstractLogic`](@ref)、[`SyntaxTree`](@ref)、[`tree`](@ref)も参照してください。
