```
@egen y1 = expr1 y2 = expr2 ... [@if condition], [by(group1, group2, ...)]
```

`df`内で新しい変数を生成するために、`expr1`、`expr2`などの式を評価します。`condition`が提供されている場合、操作は条件が真である行に対してのみ実行されます。条件が偽の場合、変数は欠損します。`by`が提供されている場合、操作はグループごとに実行されます。
