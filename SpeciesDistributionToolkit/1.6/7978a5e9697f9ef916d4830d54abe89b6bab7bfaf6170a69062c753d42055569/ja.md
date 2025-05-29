```
SimpleSDMLayers.SDMLayer(data::R, future::F; kwargs...) where {R <: RasterData, F <: Projection}
```

`RasterData`、`Projection`、およびキーワードのソースから`SDMLayer`としてレイヤーを読み込みます。許可されるキーワードは各`RasterData`に対してリストされています。
