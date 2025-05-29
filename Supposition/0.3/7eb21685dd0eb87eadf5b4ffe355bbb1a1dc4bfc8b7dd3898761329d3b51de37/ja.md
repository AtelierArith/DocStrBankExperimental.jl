```
target!(tc::TestCase, score::Float64)
```

`tc`を更新して、最適化中にこの`TestCase`が達成するスコアとして`score`を使用します。

!!! warning "複数の更新"
    このスコアは一度だけ設定できます！繰り返しの呼び出しは無視されます。

