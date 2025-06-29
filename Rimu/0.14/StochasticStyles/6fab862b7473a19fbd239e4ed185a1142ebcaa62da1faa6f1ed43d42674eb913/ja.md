```
Bernoulli(threshold=0.0) <: SpawningStrategy
```

ベルヌーイサンプリングを実行します。各オフダイアゴナル要素に対して、生成される期待値が生成構成上のウォーカーの数に等しくなる確率で生成を試みます。これは[`WithReplacement`](@ref)よりも効率が大幅に低下します。

生成試行の数がオフダイアゴナルの数を超える場合、この関数は[`Exact`](@ref)のように機能しますが、効率は低下します。最高のパフォーマンスを得るためには、この戦略は[`DynamicSemistochastic`](@ref)のサブ戦略として使用されるべきです。

## パラメータ

  * `threshold`はプロジェクションの閾値を設定します。

この戦略を使用した[`spawn!`](@ref)は、生成試行の数と生成の数を返します。
