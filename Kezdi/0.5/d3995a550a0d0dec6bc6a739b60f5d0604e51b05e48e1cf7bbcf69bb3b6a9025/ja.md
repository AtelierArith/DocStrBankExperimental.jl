```
@generate y = expr [@if condition]
```

`expr`を評価することで`df`に新しい変数`y`を作成します。`condition`が提供されている場合、操作は条件が真である行に対してのみ実行されます。条件が偽の場合、変数は欠損します。
