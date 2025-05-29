```
abstract type AbstractGrammarConstraint <: AbstractConstraint
```

ユーザー定義のすべての制約を表す抽象型です。各文法制約には、ツリー内の特定の位置で制約を伝播させる責任を持つ関連する [AbstractLocalConstraint](@ref) があります。文法制約は、新しいノードで [`AbstractLocalConstraint`](@ref) を投稿するために `on_new_node` を実装する必要があります。
