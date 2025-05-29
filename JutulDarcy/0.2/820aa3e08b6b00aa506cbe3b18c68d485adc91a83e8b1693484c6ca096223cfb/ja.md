```
plot_reservoir_simulation_result(model::MultiModel, res::ReservoirSimResult; wells = true, reservoir = true)
```

貯水池シミュレーション結果をプロットします。`wells=true`の場合、井戸の曲線がインタラクティブに表示されます。`reservoir=true`の場合、貯水池の量が3Dで視覚化されます。これらのオプションは組み合わせることができます。
