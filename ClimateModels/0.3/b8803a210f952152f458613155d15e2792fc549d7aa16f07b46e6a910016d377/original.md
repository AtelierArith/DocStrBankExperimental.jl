```
setup(x::AbstractModelConfig)
```

Defaults to `default_ClimateModelSetup(x)`. Can be expected to be  specialized for most concrete types of `AbstractModelConfig`

```
f=ClimateModels.RandomWalker
tmp=ModelConfig(model=f)
setup(tmp)
```
