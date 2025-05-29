```
get_current_population(brkga_data::BrkgaData,
                       population_index::Int64)::Population
```

`population_index`の人口を参照を返します。

!!! note
    この関数はC++ APIに準拠するために実装されています。ユーザーは`brkga_data.current[population_index]`を使用して人口に直接アクセスできます。


!!! warning
    人口を直接変更することは推奨されません。なぜなら、そのような変更は未定義の動作を引き起こす可能性があるからです。


# スロー

  * `ErrorException`: [`initialize!`](@ref)が呼び出されていない場合。
  * `ArgumentError`: `population_index < 1`または`population_index > num_independent_populations`の場合。
