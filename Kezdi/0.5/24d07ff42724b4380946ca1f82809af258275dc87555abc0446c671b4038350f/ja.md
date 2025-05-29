```
@collapse y1 = expr1 y2 = expr2 ... [@if condition], [by(group1, group2, ...)]
```

`df`を`expr1`、`expr2`などの式を評価することによって集約します。`condition`が提供されている場合、操作は条件が真である行に対してのみ実行されます。`by`が提供されている場合、操作はグループごとに実行されます。
