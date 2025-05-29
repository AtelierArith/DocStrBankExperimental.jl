```
dynamicmodelpredict(data::RheoFreqData, model::RheoModel)
```

Given dynamic rheology data with only frequency and model where parameters have been substituted. Returns another `RheoFreqData` instance with the predicted `Gp` and `Gpp` based on the frequencies and model given as arguments.
