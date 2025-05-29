```
assess(system::SystemModel, method::SequentialMonteCarlo, resultspecs::ResultSpec...)
```

`system`を使用して`method`データでSequential Monte Carloシミュレーションを実行し、`resultspecs`を返します。

# 引数

  * `system::SystemModel`: PRASデータ構造
  * `method::SequentialMonteCarlo`: PRAS分析のためのメソッド
  * `resultspecs::ResultSpec...`: [`Shortfall`](@ref)のような生成が欠落しているPRASメトリック

# 戻り値

  * `results::Tuple{Vararg{ResultAccumulator{SequentialMonteCarlo}}}`: PRASメトリック結果

```
