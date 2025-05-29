```
evaluate!(m::Model, df::DataFrame)
```

`m.func`を`df`で呼び出し、その結果を`DataFrame`に列`m.name`として追加します。
