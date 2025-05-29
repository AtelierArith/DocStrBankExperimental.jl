```
RecordChange <: RecordAction
```

debug for the amount of change of the iterate (see [`get_iterate`](@ref)`(s)` of the [`AbstractManoptSolverState`](@ref)) during the last iteration.

# Fields

  * `storage`                   : a [`StoreStateAction`](@ref) to store (at least) the last iterate to use this as the last value (to compute the change) serving as a potential cache shared with other components of the solver.
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `recorded_values`           : to store the recorded values

# Constructor

```
RecordChange(M=DefaultManifold();
    inverse_retraction_method = default_inverse_retraction_method(M),
    storage                   = StoreStateAction(M; store_points=Tuple{:Iterate})
)
```

with the previous fields as keywords. For the `DefaultManifold` only the field storage is used. Providing the actual manifold moves the default storage to the efficient point storage.
