```
multiverse = @explore begin
    @choose x = 1:5
    y = 2 * x + 3
    @measure z = sqrt(y)
end
```

Prepare and run a multiverse analysis.
