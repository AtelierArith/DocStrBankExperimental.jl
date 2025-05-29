```
max_rulenode_log_probability(rulenode::AbstractRuleNode, grammar::AbstractGrammar)
```

`AbstractRuleNode`内での最高の確率を計算します。つまり、各ノードとそのドメインについて、最高の確率を取得し、存在する場合はその子の確率と掛け算します。対数確率を使用しているため、対数を合計します。
