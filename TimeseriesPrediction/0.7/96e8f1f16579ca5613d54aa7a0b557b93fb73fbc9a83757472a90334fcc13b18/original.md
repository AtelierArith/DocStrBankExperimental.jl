```
crossprediction(source_train, target_train, source_pred,
                em::AbstractSpatialEmbedding; kwargs...)
```

Perform a spatio-temporal timeseries cross-prediction for `target` from `source`, using local weighted modeling [1]. This can be used for example when there are coupled spatial fields and one is used to predict the other. It is assumed that `source_train`, `target_train`, `source_pred` are all of the same type, `AbstractVector{<:AbstractArray{T, Φ}}`.

The spatio temporal delay embedding process is defined by `em`. See [`AbstractSpatialEmbedding`](@ref) for available methods and interfaces.

## Keyword Arguments

  * `ttype = KDTree` : Type/Constructor of tree structure. So far only tested with `KDTree`.
  * `method = AverageLocalModel(ω_safe)` : Subtype of [`AbstractLocalModel`](@ref).
  * `ntype = FixedMassNeighborhood(3)` : Subtype of `AbstractNeighborhood`.
  * `progress = true` : To print progress done.

## Description

The reconstructed state of `source_train[t][i,j,...]` is associated with the output value `target_train[t][i,j,...]`. This establishes a "connection" between `target` and `source`. Taking a reconstructed state of `source_pred` as query point, the function finds its neighbors in the reconstructed space of `source_train` using neighborhood `ntype`. Then, the neighbor *indices* are used to make a prediction for the corresponding value of the `target`, using the established "connection" between fields.

## Additional Interfaces

To save computation time in the case of repeated predictions with the same training set and embedding parameters we provide an additional interface that allows the user to provide an existing reconstruction and tree structure.

```julia
R = reconstruct(train_in, em)
tree = ttype(R)
params = PredictionParams(em, method, ntype, ttype)
sol = crossprediction(params, train_out, pred_in, R, tree; progress=true)
```

where `params` is an internal container with all relevant parameters.

## Performance Notes

Be careful when choosing embedding parameters as memory usage and computation time depend strongly on the resulting embedding dimension.

## References

[1] : U. Parlitz & C. Merkwirth, [Phys. Rev. Lett. **84**, pp 1890 (2000)](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.84.1890)
