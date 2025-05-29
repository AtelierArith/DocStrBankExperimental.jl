```
StoreStateAction <: AbstractStateAction
```

internal storage for [`AbstractStateAction`](@ref)s to store a tuple of fields from an [`AbstractManoptSolverState`](@ref)s

This functor possesses the usual interface of functions called during an iteration and acts on `(p, s, i)`, where `p` is a [`AbstractManoptProblem`](@ref), `s` is an [`AbstractManoptSolverState`](@ref) and `i` is the current iteration.

# Fields

  * `values`:        a dictionary to store interim values based on certain `Symbols`
  * `keys`:          a `Vector` of `Symbols` to refer to fields of `AbstractManoptSolverState`
  * `point_values`:  a `NamedTuple` of mutable values of points on a manifold to be stored in `StoreStateAction`. Manifold is later determined by `AbstractManoptProblem` passed to `update_storage!`.
  * `point_init`:    a `NamedTuple` of boolean values indicating whether a point in `point_values` with matching key has been already initialized to a value. When it is false, it corresponds to a general value not being stored for the key present in the vector `keys`.
  * `vector_values`: a `NamedTuple` of mutable values of tangent vectors on a manifold to be stored in `StoreStateAction`. Manifold is later determined by `AbstractManoptProblem` passed to `update_storage!`. It is not specified at which point the vectors are tangent but for storage it should not matter.
  * `vector_init`:   a `NamedTuple` of boolean values indicating whether a tangent vector in `vector_values`: with matching key has been already initialized to a value. When it is false, it corresponds to a general value not being stored for the key present in the vector `keys`.
  * `once`:          whether to update the internal values only once per iteration
  * `lastStored`:    last iterate, where this `AbstractStateAction` was called (to determine `once`)

To handle the general storage, use `get_storage` and `has_storage` with keys as `Symbol`s. For the point storage use `PointStorageKey`. For tangent vector storage use `VectorStorageKey`. Point and tangent storage have been optimized to be more efficient.

# Constructors

StoreStateAction(s::Vector{Symbol})

This is equivalent as providing `s` to the keyword `store_fields`, just that here, no manifold is necessity for the construction.

```
StoreStateAction(M)
```

## Keyword arguments

  * `store_fields` (`Symbol[]`)
  * `store_points` (`Symbol[]`)
  * `store_vectors` (`Symbol[]`)

as vectors of symbols each referring to fields of the state (lower case symbols) or semantic ones (upper case).

  * `p_init` (`rand(M)`)
  * `X_init` (`zero_vector(M, p_init)`)

are used to initialize the point and vector storage, change these if you use other types (than the default) for your points/vectors on `M`.

  * `once` (`true`) whether to update internal storage only once per iteration or on every update call
