```
abstract type AbstractRuleNode end
```

式木を表すための抽象型です。`AbstractRuleNode`は以下の関数を実装することが期待されています：

  * `isfilled(::AbstractRuleNode)::Bool`。このノードが保持する文法規則が曖昧でない場合、すなわちドメインサイズが1である場合に真を返します。
  * `isuniform(::AbstractRuleNode)::Bool`。このノードの子が知られている場合に真を返します。
  * `get_rule(::AbstractRuleNode)::Int`。それが表す文法規則のインデックスを返します。
  * `get_children(::AbstractRuleNode)::Vector{AbstractRuleNode}`。このノードの子を返します。

式木は[`RuleNode`](@ref)sと[`AbstractHole`](@ref)sで構成されています。

  * [`RuleNode`](@ref)は[`AbstractGrammar`](@ref)における特定の生成規則を表します。
  * [`AbstractHole`](@ref)は文法の特定の規則がまだ適用できるプレースホルダーです。
