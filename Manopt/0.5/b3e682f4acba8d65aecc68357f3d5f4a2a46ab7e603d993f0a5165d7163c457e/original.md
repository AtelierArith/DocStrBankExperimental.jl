```
mesh_adaptive_direct_search(M, f, p=rand(M); kwargs...)
mesh_adaptive_direct_search(M, mco::AbstractManifoldCostObjective, p=rand(M); kwargs..)
mesh_adaptive_direct_search!(M, f, p; kwargs...)
mesh_adaptive_direct_search!(M, mco::AbstractManifoldCostObjective, p; kwargs..)
```

The Mesh Adaptive Direct Search (MADS) algorithm minimizes an objective function $f: \mathcal M → ℝ$ on the manifold `M`. The algorithm constructs an implicit mesh in the tangent space $T_{p}\mathcal M$ at the current candidate $p$. Each iteration consists of a search step and a poll step.

The search step selects points from the implicit mesh and attempts to find an improved candidate solution that reduces the value of $f$. If the search step fails to generate an improved candidate solution, the poll step is performed. It consists of a local exploration on the current implicit mesh in the neighbourhood of the current iterate.

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `p`: a point on the manifold $\mathcal M$

# Keyword arguments

  * `mesh_basis=`[`DefaultOrthonormalBasis`](@extref `ManifoldsBase.DefaultOrthonormalBasis`): a basis to generate the mesh in. The mesh is generated in coordinates of this basis in every tangent space
  * `max_stepsize=`[`injectivity_radius`](@extref `ManifoldsBase.injectivity_radius-Tuple{AbstractManifold}`)`(M)`: a maximum step size to take. any vector generated on the mesh is shortened to this length to avoid leaving the injectivity radius,
  * `poll::`[`AbstractMeshPollFunction`](@ref)`=`[`LowerTriangularAdaptivePoll`](@ref)`(M, copy(M,p))`: the poll function to use. The `mesh_basis` (as `basis`), `retraction_method`, and `vector_transport_method` are passed to this default as well.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `scale_mesh=`[`injectivity_radius`](@extref `ManifoldsBase.injectivity_radius-Tuple{AbstractManifold}`)`(M) / 4`: initial scaling of the mesh
  * `search::`[`AbstractMeshSearchFunction`](@ref)`=`[`DefaultMeshAdaptiveDirectSearch`](@ref)`(M, copy(M,p))`: the search function to use. The `retraction_method` is passed to this default as well.
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(500)`[`|`](@ref StopWhenAny)[`StopWhenPollSizeLess`](@ref)`(1e-10)`: a functor indicating that the stopping criterion is fulfilled
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
