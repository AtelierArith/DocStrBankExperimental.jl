```
barabasi_albert(n, k, G=Graph; seed=-1)
barabasi_albert(n, n0, k, G=Graph; seed=-1)
```

`n` 頂点を持つタイプ `G` のランダムグラフを [Barabási–Albert モデル](https://en.wikipedia.org/wiki/Barab%C3%A1si%E2%80%93Albert_model) に従って作成します。これは、最初のグラフに `n0` 頂点を追加することで成長します（指定されていない場合、`n0=k` となります）。新しい頂点は、優先的接続によってシステム内に既に存在する `k` つの異なる頂点に `k` 本のエッジで接続されます。初期グラフはデフォルトで空です。

デフォルトでは無向グラフが作成されます。最後の引数として有向グラフタイプ（例：`DiGraph`）を渡すことで、有向グラフを作成できます。

与えられたグラフを成長させるための [`barabasi_albert!`](@ref) も参照してください。
