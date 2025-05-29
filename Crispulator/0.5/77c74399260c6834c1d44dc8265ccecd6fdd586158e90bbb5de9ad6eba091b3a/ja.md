```julia
select(
    setup,
    initial_cells,
    initial_cell_phenotypes,
    guides
)

```

与えられた集団 `initial_cells` と `initial_cell_phenotypes` に対して、この関数は [GrowthScreen](@ref) の選択ステップをモデル化します。細胞はその成長表現型に従って倍増することが許可され、その後、`setup` で定義された `bottleneck_representation` を維持するために集団がサブサンプリングされます。倍増とサブサンプリングの回数は、`setup` の `num_bottlenecks` パラメータによって制御されます。

したがって、ボトルネックが3つあり、`length(initial_cells) == bottleneck_representation` の場合、次のような動作が期待されます：

```
           Cell population
```

┌────────────────────────────────────────┐ 2 │           .-           .r|          ..|│   │         r*`|         _-' |        .r/ |│   │       ."   |       .*    |      .r'   |│   │    .-"      |    ,"`|    ,/'     |│   │  _-`        | .-/        |  .*`       |│ 1 │_*           Lr'          |r/          |│   └────────────────────────────────────────┘    0                                      3                  Bottleneck #

もし `initial_cells` によるライブラリのカバレッジが `bottleneck_representation` よりも少ない場合、集団はパッセージングが必要になるまで、または `num_bottlenecks` に達するまで、どちらか早い方まで倍増することが許可されます。
