```
launch(x)
```

Defaults to `default_ClimateModelLaunch(x)` which consists in `take!(x)` for `AbstractModelConfig`. Can be expected to be specialized for most  concrete types of `AbstractModelConfig`

```
f=ClimateModels.RandomWalker
tmp=ModelConfig(model=f)
setup(tmp)
build(tmp)
launch(tmp)
```
