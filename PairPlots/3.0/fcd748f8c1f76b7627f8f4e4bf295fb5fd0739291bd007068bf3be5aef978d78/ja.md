```
pairplot(inputs...; figure=(;), kwargs...)
```

新しいMakieフィギュアを解像度(800,800)で生成し、その後通常通り`pairplot`を呼び出すための便利なメソッドです。フィギュアを返します。

例:

```julia
fig = pairplot(table)
```
