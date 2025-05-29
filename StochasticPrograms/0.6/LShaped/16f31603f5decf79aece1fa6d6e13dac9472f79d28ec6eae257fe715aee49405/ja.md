```
DynamicAggregation
```

動的集約をL字型アルゴリズムで使用するためのファンクタオブジェクト。`LShaped.Optimizer`の`aggregate`を通じて[`DynamicAggregate`](@ref)オブジェクトを供給するか、[`Aggregator`](@ref)属性を設定することで作成されます。

以下の選択ルールが利用可能です

  * [`SelectUniform`](@ref)
  * [`SelectDecaying`](@ref)
  * [`SelectRandom`](@ref)
  * [`SelectClosest`](@ref)
  * [`SortByReference`](@ref)

...

# パラメータ

  * `num_aggregates::Int`: 集約の数
  * `rule::SelectionRule`: 入ってくるカットがどの集約に配置されるべきかを決定するルール
  * `lock_after::Function = (τ,n)->false`: 現在の最適性ギャップ`τ`と反復回数`n`に基づいて、現在の集約スキームを固定すべきかどうかを決定する関数

...
