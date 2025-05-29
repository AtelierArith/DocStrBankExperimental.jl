```
RandomWalker(x::AbstractModelConfig)
```

2Dのランダムウォークを`NS`ステップ（デフォルトは100）で実行します。結果は配列とテキストファイルとして提供されます。

デフォルトでは、`RandomWalker.csv`が`pathof(x)`に作成されます。そのフォルダ自体は、以下のように`run`を介して`setup`によって作成されます。

```
MC=ModelConfig(ClimateModels.RandomWalker)
run(MC)
```
