```
DynamicSemistochastic(; strat, rel_threshold, abs_threshold) <: SpawningStrategy
```

[`SpawningStrategy`](@ref) は、ウォーカーの数が少ないときは `strat` のように振る舞い、ウォーカーの数が多いときは正確なステップを実行します。「多い」とは、以下に説明する2つの閾値によって制御されます。

## パラメータ

  * `strat = WithReplacement()`: 正確に乗算が行われない場合に使用する [`SpawningStrategy`](@ref) です。`strat` にゼロ以外の `threshold` がある場合、すべてのスポーンはその閾値に投影されます。
  * `rel_threshold = 1.0`: 正確なスポーンを実行するかどうかを決定する際に、この値がウォーカーの数に掛けられます。最良のパフォーマンスのためには1以上に設定する必要があります。この閾値は、[`spawn!`](@ref) の `boost` 引数の影響を受けます。
  * `abs_threshold = Inf`: 正確なスポーンを実行するかどうかを決定する際に、`min(abs_threshold, num_offdiagonals)` が使用されます。この閾値は、[`spawn!`](@ref) の `boost` 引数の影響を受けません。

例えば、`strat.threshold` パラメータの説明については、[`WithoutReplacement`](@ref) を参照してください。

この戦略を使用した [`spawn!`](@ref) は、正確なスポーンと不正確なスポーンの数、スポーン試行の数、およびスポーンの数を返します。
