```
dual_number(X, p; backend=PrunedFIsBackend(), direction=nothing)
dual_number(p; backend=PrunedFIsBackend(), direction=nothing)
```

[`stochastic_triple`](#StochasticAD.stochastic_triple) の周りの軽量ラッパーで、すべての離散ランダムコンポーネントの導関数の寄与を完全に無視するため、通常の双対数のように振る舞います。主に楽しみのために – もちろん、これは離散ランダム関数に対して無用な導関数の推定につながります！
