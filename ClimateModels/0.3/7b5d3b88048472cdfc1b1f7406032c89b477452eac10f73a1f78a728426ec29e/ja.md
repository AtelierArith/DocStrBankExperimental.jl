```
take!(x :: AbstractModelConfig)
```

x.channel からコマンド `v` を取得し (すなわち `take!(x.channel)`)、`v(x)` を実行します (もしそれが関数であれば) または `v` を返します (もし関数でなければ、例えば文字列など)。

```
tmp=ModelConfig()
put!(tmp,ClimateModels.RandomWalker)
take!(tmp)
```
