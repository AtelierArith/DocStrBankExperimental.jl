```
multiverse = @explore begin
    @choose x = 1:5
    y = 2 * x + 3
    @measure z = sqrt(y)
end
```

マルチバース分析を準備して実行します。
