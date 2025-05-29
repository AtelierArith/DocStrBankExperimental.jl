```
WithReplacement(threshold=0.0) <: SpawningStrategy
```

[`SpawningStrategy`](@ref) は、スポーンターゲットがリプレースメントでサンプリングされる戦略です。これは、ほとんどの[`StochasticStyle`](@ref)のデフォルトのスポーニング戦略です。

## パラメータ

  * `threshold` はプロジェクションの閾値を設定します。ゼロに設定すると、プロジェクションは行われません。

この戦略を使用した[`spawn!`](@ref)は、スポーン試行の回数とスポーンの回数を返します。
