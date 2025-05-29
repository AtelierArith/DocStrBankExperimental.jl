```
isfilled(node::AbstractRuleNode)::Bool
```

[`AbstractRuleNode`]が単一のルールを保持しているかどうかを返します。これは常に[`RuleNode`](@ref)に当てはまります。穴は、そのドメインサイズが正確に1である場合に「埋まっている」と見なされます。
