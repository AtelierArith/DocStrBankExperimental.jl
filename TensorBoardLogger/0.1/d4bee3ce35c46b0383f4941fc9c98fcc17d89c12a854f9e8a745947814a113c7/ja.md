```
log_histogram(logger, name, (bins,weights); step=step(logger))
```

指定された `step` で `name` タグの下にヒストグラムをログします。ヒストグラムは、`N+1` のビンのエッジと `N` のビンの高さを保持するタプルとして渡す必要があります。

生データを渡すこともでき、その場合は `StatsBase.jl` からのビニングアルゴリズムがデータをビンに分けるために使用されます。
