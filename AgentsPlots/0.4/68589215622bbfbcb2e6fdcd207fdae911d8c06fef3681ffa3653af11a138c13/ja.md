```
plotabm(model::ABM{<: GraphSpace}; ac, as, am, kwargs...)
```

この関数は `ContinuousSpace` の `plotabm` と同じですが、ここでは3つの主要な関数 `ac, as, am` がエージェントを入力として受け取るのではなく、グラフの各ノードにおけるエージェントのベクトルを受け取ります。出力は同じです。

ここで `as` はデフォルトで `length` になります。内部的には、`graphplot` レシピが使用され、他のすべての `kwargs...` はそこに伝播されます。
