```
AutoChainRules{RC}
```

[ChainRulesCore.jl](https://github.com/JuliaDiff/ChainRulesCore.jl)に基づいて自動微分バックエンドを選択するために使用される構造体（リストは[こちら](https://juliadiff.org/ChainRulesCore.jl/stable/index.html#ChainRules-roll-out-status)を参照）。

[ADTypes.jl](https://github.com/SciML/ADTypes.jl)によって定義されています。

# コンストラクタ

```
AutoChainRules(; ruleconfig)
```

# フィールド

  * `ruleconfig::RC`: [`ChainRulesCore.RuleConfig`](https://juliadiff.org/ChainRulesCore.jl/stable/rule_author/superpowers/ruleconfig.html)オブジェクト。
