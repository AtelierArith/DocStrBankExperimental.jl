```
@newmodelsingleton name parent
```

A macro that defines an EoSModel without any fields ("singleton" struct.). useful for defining EoS that don't use any parameters, while being composable with other `EoSModels`.
