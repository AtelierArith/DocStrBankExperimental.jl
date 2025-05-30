```
ContinuousResourceSharer{T}(nports, nstates, f, portmap)
```

無向オープン連続システム。ダイナミクス関数 `f` はODE $\dot u(t) = f(u(t),p,t)$ を定義し、ここで $u(t)$ の長さは `nstates` です。`nports` は公開ポートの数で、`portmap` は公開状態のリストです。例えば、`portmap = [2,2,3]` の場合、状態変数 2, 2, 3 をそれぞれ公開する3つのポートがあります。
