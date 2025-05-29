```
fit(::Type{BayesNet}, data, edges)
```

データの列が変数であり、エッジがedgesで与えられるベイジアンネットをフィットします。

```
ex: fit(DiscreteBayesNet, data, (:A=>:B, :C=>B))
```
