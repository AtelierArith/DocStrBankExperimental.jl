```
setup(x::AbstractModelConfig)
```

デフォルトは `default_ClimateModelSetup(x)` です。ほとんどの具体的な `AbstractModelConfig` の型に対して特化されることが期待されます。

```
f=ClimateModels.RandomWalker
tmp=ModelConfig(model=f)
setup(tmp)
```
