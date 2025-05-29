```
squash(g::Union{SimpleGraph, SimpleDiGraph}; alwayscopy=true)
```

`SimpleGraph` と `SimpleDiGraph` のための `Graphs.squash` の特化版です。`alwayscopy` が `true` の場合、結果のグラフは常にコピーになります。そうでない場合、元のグラフであることもあります。
