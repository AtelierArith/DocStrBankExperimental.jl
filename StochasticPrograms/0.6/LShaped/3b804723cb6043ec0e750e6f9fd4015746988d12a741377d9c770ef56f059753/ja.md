```
ClusterAggregation
```

L字型アルゴリズムでクラスタ集約を使用するためのファンクタオブジェクト。`LShaped.Optimizer`の`aggregate`を通じて[`ClusterAggregate`](@ref)オブジェクトを供給するか、[`Aggregator`](@ref)属性を設定することで作成されます。

以下のクラスタルールが利用可能です

  * [`StaticCluster`](@ref)
  * [`ClusterByReference`](@ref)
  * [`Kmedoids`](@ref)
  * [`Hierarchical`](@ref)

...

# パラメータ

  * `rule::ClusterRule`: カットをクラスタにどのようにソートするかを決定するルール
  * `lock_after::Function = (τ,n)->false`: 現在の最適性ギャップ`τ`と反復回数`n`に基づいて、現在の集約スキームを固定すべきかどうかを決定する関数

...
