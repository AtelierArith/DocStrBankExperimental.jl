```julia
setValKDE!(vd, pts, bws)
setValKDE!(vd, pts, bws, setinit)
setValKDE!(vd, pts, bws, setinit, ipc)

```

変数ノードの点の中心とバンド幅パラメータを設定し、`setinit::Bool=true`の場合は`isInitialized=true`に設定します（デフォルト通り）。

ノート

  * `initialized`は、変数がまだ初期化されていないファクターグラフの初期解決に使用されます。
  * `inferdim`は、初期化が部分的であったかどうかを識別するために使用されます。
