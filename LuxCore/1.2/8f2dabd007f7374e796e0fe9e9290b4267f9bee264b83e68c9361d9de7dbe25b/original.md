```
abstract type AbstractLuxLayer
```

Abstract Type for all Lux Layers

Users implementing their custom layer, **must** implement

  * `initialparameters(rng::AbstractRNG, layer::CustomAbstractLuxLayer)` – This returns a `NamedTuple` containing the trainable parameters for the layer.
  * `initialstates(rng::AbstractRNG, layer::CustomAbstractLuxLayer)` – This returns a NamedTuple containing the current state for the layer. For most layers this is typically empty. Layers that would potentially contain this include `BatchNorm`, `LSTM`, `GRU`, etc.

Optionally:

  * `parameterlength(layer::CustomAbstractLuxLayer)` – These can be automatically calculated, but it is recommended that the user defines these.
  * `statelength(layer::CustomAbstractLuxLayer)` – These can be automatically calculated, but it is recommended that the user defines these.

See also [`AbstractLuxContainerLayer`](@ref)
