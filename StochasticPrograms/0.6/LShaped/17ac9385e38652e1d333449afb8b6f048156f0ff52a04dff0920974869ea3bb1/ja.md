```
HybridAggregation
```

L字型アルゴリズムでハイブリッド集約を使用するためのファンクタオブジェクト。`LShaped.Optimizer`の`aggregate`を通じて[`HybridAggregate`](@ref)オブジェクトを供給するか、[`Aggregator`](@ref)属性を設定することで作成されます。

...

# パラメータ

  * `initial::AbstractAggregator`: 初期集約スキーム
  * `final::AbstractAggregator`: 最終集約スキーム
  * `τ::T`: 最適性ギャップが`τ`未満に減少したときに、アクティブな集約スキームが`initial`から`final`に切り替わります

...
