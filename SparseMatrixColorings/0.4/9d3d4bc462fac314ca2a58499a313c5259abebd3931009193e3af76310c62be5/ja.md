```
RandomOrder(rng=default_rng(), seed=nothing)
```

[`AbstractOrder`](@ref) のインスタンスで、与えられた `seed` で `rng` から生成されたランダムな順列を使用して頂点をソートします。

  * `seed = nothing` の場合、`rng` は再シードされません。したがって、`vertices(g, order)` への2回の連続した呼び出しは異なる結果を返します。
  * それ以外の場合、各サンプルの前に `rng` は再シードされます。したがって、`vertices(g, order)` への2回の連続した呼び出しは同じ結果を返します。

!!! warning
    `default_rng()` でシードを使用しないでください。そうしないと、プログラムのグローバルな状態に影響を与えます。再現性が必要な場合は、`RandomOrder` 用に特別に新しい `rng` を作成してください。パッケージ [StableRNGs.jl](https://github.com/JuliaRandom/StableRNGs.jl) は、Julia のバージョン間で動作が安定している乱数生成器を提供します。

