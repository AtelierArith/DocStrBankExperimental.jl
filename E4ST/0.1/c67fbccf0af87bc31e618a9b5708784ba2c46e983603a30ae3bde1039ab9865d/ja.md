```
get_egen_gen(data, model, gen_idx)
```

指定された発電所からの総エネルギー生成を、すべての代表時間にわたって合計して返します。

```
get_egen_gen(data, model, gen_idx, year_idx)
```

指定された年の代表時間にわたって合計した、指定された発電所からの総エネルギー生成を返します。

```
get_egen_gen(data, model, gen_idx, year_idx, hour_idx)
```

指定された年と時間に対する、指定された発電所からの総エネルギー生成を返します。これは、pgen*genに、その代表時間で費やされた時間数を掛けたものです。詳細は[`get*hour_weight`](@ref)を参照してください。

  * モデルが最適化された後に変数の値を取得するには、次のように`value()`で関数をラップします: `value.(get_egen_gen(args...))`。
