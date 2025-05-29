```
RasterData{P <: RasterProvider, D <: RasterDataset}
```

The `RasterData` type is the main user-facing type for `SimpleSDMDatasets`. Specifically, this is a *singleton* parametric type, where the two parameters are the type of the `RasterProvider` and the `RasterDataset`. Note that the inner constructor calls the `provides` method on the provider/dataset pair to check that this combination exists.
