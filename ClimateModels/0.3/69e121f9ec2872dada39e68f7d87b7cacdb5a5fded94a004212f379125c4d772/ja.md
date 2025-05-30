```
launch(x)
```

デフォルトは `default_ClimateModelLaunch(x)` で、`AbstractModelConfig` の `take!(x)` で構成されています。ほとんどの具体的な `AbstractModelConfig` の型に対して特化されることが期待されます。

```
f=ClimateModels.RandomWalker
tmp=ModelConfig(model=f)
setup(tmp)
build(tmp)
launch(tmp)
```
