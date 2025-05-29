```
DefaultMeshAdaptiveDirectSearch <: AbstractMeshSearchFunction
```

# Functor

```
(s::DefaultMeshAdaptiveDirectSearch)(problem, mesh_size::Real, X; scale_mesh::Real=1.0, max_stepsize::Real=inf)
```

# Fields

  * `q`: a temporary memory for a point on the manifold
  * `X`: information to perform the search, e.g. the last direction found by poll.
  * `last_search_improved::Bool` indicate whether the last search was successful, i.e. improved the cost.
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)

# Constructor

```
DefaultMeshAdaptiveDirectSearch(M::AbstractManifold, p=rand(M); kwargs...)
```

## Keyword arguments

  * `X::T=zero_vector(M, p)
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
