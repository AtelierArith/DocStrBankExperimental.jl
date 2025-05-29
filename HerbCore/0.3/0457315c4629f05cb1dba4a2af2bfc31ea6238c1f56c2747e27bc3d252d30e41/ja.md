```
RuleNode <: AbstractRuleNode
```

[`RuleNode`](@ref)は、式木のノードを表します。各ノードは、[`AbstractGrammar`](@ref)内の特定のルールに対応しています。[`RuleNode`](@ref)は以下で構成されています：

  * `ind`: このノードが表している[`AbstractGrammar`](@ref)内のルールのインデックス。
  * `_val`: `RuleNode`の評価をキャッシュするためのフィールドで、複数の不必要な評価を防ぎます。このフィールドは、必要な情報を格納するために使用できます。
  * `children`: 式木内のこのノードの子ノード

!!! compat
    即時評価機能は、現在ほとんどのHerb.jlではサポートされていません。

