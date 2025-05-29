```
RuleNode(ind::Int, _val::Any)
```

[`RuleNode`](@ref)を、インデックス`ind`の[`AbstractGrammar`](@ref)ルールのために作成し、`_val`を即時評価された値とし、子供を持たない

!!! warning
    ルールが終端であり、子供を持たないことが絶対に確実な場合にのみ、このコンストラクタを使用してください。子供を持つ可能性のあるルールには[`RuleNode(ind::Int, grammar::AbstractGrammar)`]を使用してください。一般的に、子供がまだ知られていないノードのプレースホルダーとして[`AbstractHole`](@ref)を使用するべきです。


!!! compat
    即時評価機能は、まだほとんどのHerb.jlではサポートされていません。

