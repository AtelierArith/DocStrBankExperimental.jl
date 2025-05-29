```
watts_strogatz(n, k, β, G=Graph; seed=-1)
```

`n` 頂点を持ち、各頂点の次数が `k` である [Watts-Strogatz](https://en.wikipedia.org/wiki/Watts_and_Strogatz_model) 小モデルランダムグラフを作成します。エッジは確率 `β` に基づいてモデルに従ってランダム化されます。

デフォルトでは無向グラフが作成されます。有向グラフは、最後の引数として有向グラフタイプ（例：`DiGraph`）を渡すことで作成できます。
