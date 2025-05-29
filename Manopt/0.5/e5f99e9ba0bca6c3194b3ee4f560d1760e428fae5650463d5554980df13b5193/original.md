```
LowerTriangularAdaptivePoll <: AbstractMeshPollFunction
```

Generate a mesh (poll step) based on Section 6 and 7 of [Dreisigmeyer:2007](@cite), with two small modifications:

  * The mesh can be scaled globally so instead of $Δ_0^m=1$ a certain different scale is used
  * Any poll direction can be rescaled if it is too long. This is to not exceed the injectivity radius for example.

# Functor

```
(p::LowerTriangularAdaptivePoll)(problem, mesh_size; scale_mesh=1.0, max_stepsize=inf)
```

# Fields

  * `base_point::P`: a point on the manifold, where the mesh is build in the tangent space
  * `basis`: a basis of the current tangent space with respect to which the mesh is stored
  * `candidate::P`: a memory for a new point/candidate
  * `mesh`: a vector of tangent vectors storing the mesh.
  * `random_vector`: a $d$-dimensional random vector $b_l$`
  * `random_index`: a random index $ι$
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `vector_transport_method::AbstractVectorTransportMethodP`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `X::T` the last successful poll direction stored as a tangent vector. initialised to the zero vector and reset to the zero vector after moving to a new tangent space.

# Constructor

```
LowerTriangularAdaptivePoll(M, p=rand(M); kwargs...)
```

## Keyword arguments

  * `basis=`[`DefaultOrthonormalBasis`](@extref `ManifoldsBase.DefaultOrthonormalBasis`)
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$
