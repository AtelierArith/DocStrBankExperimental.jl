```
SourceTerm(cell, value; fractional_flow = [1.0], type = MassSource)
```

指定された `cell` に指定された合計 `value` でソース項を作成します。

オプションの `fractional_flow` 引数は、この項が流入に使用される場合に成分にどのように分割されるかを制御し、システム内の各成分ごとに1つのエントリを含む必要があります: (`number_of_components(system)`)。 `fractional_flow` は 1.0 に合計される必要があります。 `type` 引数は `FlowSourceType` 列挙型のインスタンスである必要があり、解釈は次のとおりです。

  * `MassSource`: ソースは成分の質量として直接解釈されます。
  * `StandardVolumeSource`: ソースは標準/表面条件での体積です。 参照密度が質量ソースに変換するために使用されます。
  * `VolumeSource`: ソースはその場/貯留条件での体積です。
