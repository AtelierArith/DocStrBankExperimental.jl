```
set_inputs!(mg::MetaGraphsNext.MetaGraph; α::Float64=0.0)
```

mgの各サブグラフ/頂点に共有値を設定します：

1. 現在の頂点のv0をその隣接頂点の電圧に設定します
2. 現在の頂点のP/Qloadを隣接頂点の変電所バス負荷に設定します
