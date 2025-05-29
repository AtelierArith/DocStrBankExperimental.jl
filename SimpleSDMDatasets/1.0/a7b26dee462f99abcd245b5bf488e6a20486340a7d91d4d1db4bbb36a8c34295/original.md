```
Future{S <: FutureScenario, M <: FutureModel}
```

This type is similar to `RasterData` but describes a combination of a scenario and a model. Note that *unlike* `RasterData`, there is no type check in the inner constructor; instead, the way to check that a provider/dataset/scenario/model combination exists is to overload the `provides` method for a dataset and future.
