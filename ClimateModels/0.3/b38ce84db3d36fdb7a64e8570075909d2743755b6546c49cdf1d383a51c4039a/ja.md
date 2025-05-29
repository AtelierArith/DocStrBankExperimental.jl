```
clean(x :: AbstractModelConfig)
```

残りのタスクをキャンセルします (x.channel) および実行ディレクトリを削除します (pathof(x))

```
tmp=ModelConfig(model=ClimateModels.RandomWalker)
setup(tmp)
clean(tmp)
```
