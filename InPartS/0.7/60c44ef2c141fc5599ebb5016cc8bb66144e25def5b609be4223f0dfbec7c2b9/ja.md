```
autogrid!(sim, lsize, params, spacing = 1.0, rng = sim.rng, kwargs...)
```

`sim`に`N`次元の直交格子に配置された粒子を追加します。

これは本質的にaddgrid!を呼び出しますが、指定されたパラメータのいずれかに対して`distance`を最大の`minimumgridconstant`として選択し（`spacing`で乗算）、モデル定義の`defaultgridinitialization`関数で粒子を初期化します。

`rng`は`addgrid!`のための`_jitter_rng`として使用され、`defaultgridinitialization`に渡されます。
