```
setup(rng::AbstractRNG, layer)
```

レイヤー `l` のパラメータと状態を取得するための省略形です。`(initialparameters(rng, l), initialstates(rng, l))` と同等です。

!!! warning
    この関数は純粋ではなく、`rng` を変更します。

