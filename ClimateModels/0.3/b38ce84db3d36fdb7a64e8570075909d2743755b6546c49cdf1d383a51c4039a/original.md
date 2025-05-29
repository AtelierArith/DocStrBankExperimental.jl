```
clean(x :: AbstractModelConfig)
```

Cancel any remaining task (x.channel) and rm the run directory (pathof(x))

```
tmp=ModelConfig(model=ClimateModels.RandomWalker)
setup(tmp)
clean(tmp)
```
