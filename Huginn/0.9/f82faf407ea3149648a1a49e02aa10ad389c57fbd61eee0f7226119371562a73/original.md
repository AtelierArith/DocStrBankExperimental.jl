function initialize*iceflow*model!(     iceflow*model::IF,     glacier*idx::I,     glacier::AbstractGlacier,     params::Sleipnir.Parameters ) where {IF <: IceflowModel, I <: Integer}

Initialize iceflow model data structures to enable in-place mutation.

# Keyword arguments

```
- `iceflow_model`: Iceflow model used for simulation.
- `glacier_idx`: Index of glacier.
- `glacier`: `Glacier` to provide basic initial state of the ice flow model.
- `parameters`: `Parameters` to configure some physical variables.
```
