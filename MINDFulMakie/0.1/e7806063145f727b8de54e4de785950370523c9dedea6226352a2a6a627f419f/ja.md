```
intentplot(ibn::IBN, idx::Integer)
intentplot!(ax, ibn::IBN, idx::Integer)
```

意図の有向非巡回グラフ (DAG) `idx` のツリープロットを作成します。

## 属性

  * `interdomain=false`: すべてのドメインにアクセスします (動作しない可能性があります)
  * `show_state=true`: 各意図DAGノードの状態を表示します
