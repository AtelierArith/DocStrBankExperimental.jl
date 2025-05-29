```
AdvancedParticleFilter(N::Integer, dynamics::Function, measurement::Function, measurement_likelihood, dynamics_density, initial_density; p = NullParameters(), threads = false, kwargs...)
```

この型は標準的な粒子フィルタを表しますが、[`ParticleFilter`](@ref)型と比較して、動的および測定関数における非加法的ノイズなど、追加の柔軟性を提供します。

詳細については、ドキュメントを参照してください: https://baggepinnen.github.io/LowLevelParticleFilters.jl/stable/#AdvancedParticleFilter-1

# 引数:

  * `N`: 粒子の数
  * `dynamics`: 離散時間の動的関数 `(x, u, p, t, noise=false) -> x⁺`。`noise`引数がデフォルトで`false`であることが重要です。
  * `measurement`: 測定関数 `(x, u, p, t, noise=false) -> y`。`noise`引数がデフォルトで`false`であることが重要です。
  * `measurement_likelihood`: 測定の対数尤度を評価する関数 `(x, u, y, p, t)->logl`。
  * `dynamics_density`: このフィールドは高度なフィルタでは使用されず、`nothing`に設定できます。
  * `initial_density`: 初期状態の分布。
  * `threads`: 粒子を並行して伝播させるためにスレッドを使用します。動的がスレッドセーフである場合のみこれを有効にしてください。`SeeToDee.SimpleColloc`は内部キャッシュの使用によりデフォルトではスレッドセーフではありませんが、`SeeToDee.Rk4`はスレッドセーフです。

# 拡張ヘルプ

## 複数の測定モデル

`measurement_likelihood`関数は、測定の尤度を評価するために使用されます。複数のセンサーがあり、それぞれに対して個別の`correct!`ステップを実行したい場合は、`correct!(..., g = custom_likelihood_function)`を呼び出してください。
