```
SimpleSDMLayers.SDMLayer(data::R, future::F; kwargs...) where {R <: RasterData, F <: Projection}
```

Read a layer as a `SDMLayer` from a `RasterData`, a `Projection`, and a source of keywords. The allowed keywords are listed for each `RasterData`.
