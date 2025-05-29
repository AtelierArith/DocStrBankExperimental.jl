```
deformspace(domain, localaniso, metric; kwargs)
deformspace(domain, localaniso, metric, refvariogram; kwargs)
```

deformspace(samples, domain, localaniso, metric; kwargs)     deformspace(samples, domain, localaniso, metric, refvariogram; kwargs)     deformspace(graphobject, metric=GraphDistance; kwargs)   kwargs = (anchors=1500, maxoutdim=200, weights=nothing)

Spatial deformation is a method that transforms coordinates to an isotropic space in high dimension where the local anisotropies information are embedded into the new distances. Traditional estimations and simulations can be performed in this new data configuration. It's necessary to inform the `domain` object (and the `samples` if applied). The local anisotropies are passed via `localaniso` and `metric` define how the local anisotropies are used to calculate the new data distances. Available metrics to calculate distance between two points are:

  * `AnisoDistance`   - averaged anisotropic distance
  * `KernelVariogram` - non-stationary variogram kernel estimator
  * `GraphDistance`   - geodesic distances of a informed graph. More details of the graph construction in [`graph`](@ref) docstring.

A reference variogram `refvariogram` is necessary if metric is `KernelVariogram`. Additional keyword arguments are the number of `anchors` to perform landmark MDS if the number of data is too big for a traditional MDS. `maxoutdim` is the maximum number of dimensions to retain after MDS. `weights` are the declustering weights of the domain data (+ samples) in order to help selecting declustered anchor points for the transformations.
