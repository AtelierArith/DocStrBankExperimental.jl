```julia
simulate(
    model,
    parameters;
    n_steps,
    stop,
    init,
    tracked,
    rng,
    kw...
)

```

名前付きタプル `(; data, logp)` を返します。`stop(data, i)` は、シミュレーションされた `data` のシーケンスとイテレーションカウンタ `i` に依存するブール関数です。`tracked = true` の場合、モデルの状態はシミュレーションの各ステップで保存されます。追加のキーワード引数 `kw` は `sample` 関数に渡されます。
