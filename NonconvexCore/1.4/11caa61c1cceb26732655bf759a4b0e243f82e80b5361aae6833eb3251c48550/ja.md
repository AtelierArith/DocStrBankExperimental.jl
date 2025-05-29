```
addvar!(model::AbstractModel, lb::Number, ub::Number; init = lb, integer = false)
```

`model`に新しい変数を追加します。下限と上限はそれぞれ`lb`と`ub`、初期値は`init`、変数が整数の場合は`integer = true`です。
