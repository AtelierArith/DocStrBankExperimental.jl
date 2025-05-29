```
patricle_swarm(M, f; kwargs...)
patricle_swarm(M, f, swarm; kwargs...)
patricle_swarm(M, mco::AbstractManifoldCostObjective; kwargs..)
patricle_swarm(M, mco::AbstractManifoldCostObjective, swarm; kwargs..)
particle_swarm!(M, f, swarm; kwargs...)
particle_swarm!(M, mco::AbstractManifoldCostObjective, swarm; kwargs..)
```

perform the particle swarm optimization algorithm (PSO) to solve

$$
\operatorname*{arg\,min}_{p ∈ \mathcal M} f(p)
$$

PSO starts with an initial `swarm` [BorckmansIshtevaAbsil:2010](@cite) of points on the manifold. If no `swarm` is provided, the `swarm_size` keyword is used to generate random points. The computation can be perfomed in-place of `swarm`.

To this end, a swarm $S = \{s_1, \ldots, s_n\}$ of particles is moved around the manifold `M` in the following manner. For every particle $s_k^{(i)}$ the new particle velocities $X_k^{(i)}$ are computed in every step $i$ of the algorithm by

$$
X_k^{(i)} = ω \mathcal T_{s_k^{(i)←s_k^{(i-1)}} X_k^{(i-1)} + c r_1  \operatorname{retr}^{-1}_{s_k^{(i)}}(p_k^{(i)}) + s r_2 \operatorname{retr}^{-1}_{s_k^{(i)}}(p),
$$

where

  * $s_k^{(i)}$ is the current particle position,
  * $ω$ denotes the inertia,
  * $c$ and $s$ are a cognitive and a social weight, respectively,
  * $r_j$, $j=1,2$ are random factors which are computed new for each particle and step
  * \mathcal T_{⋅←⋅} is a vector transport, and
  * \operatorname{retr}^{-1} is an inverse retraction

Then the position of the particle is updated as

$$
s_k^{(i+1)} = \operatorname{retr}_{s_k^{(i)}}(X_k^{(i)}),
$$

Then the single particles best entries $p_k^{(i)}$ are updated as

$$
p_k^{(i+1)} = \begin{cases}
s_k^{(i+1)},  & \text{if } F(s_k^{(i+1)})<F(p_{k}^{(i)}),\\
p_{k}^{(i)}, & \text{else,}
\end{cases}
$$

and the global best position

$$
g^{(i+1)} = \begin{cases}
p_k^{(i+1)},  & \text{if } F(p_k^{(i+1)})<F(g_{k}^{(i)}),\\
g_{k}^{(i)}, & \text{else,}
\end{cases}
$$

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `swarm = [rand(M) for _ in 1:swarm_size]`: an initial swarm of points.

Instead of a cost function `f` you can also provide an [`AbstractManifoldCostObjective`](@ref) `mco`.

# Keyword Arguments

  * `cognitive_weight=1.4`: a cognitive weight factor
  * `inertia=0.65`: the inertia of the particles
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `social_weight=1.4`: a social weight factor
  * `swarm_size=100`: swarm size, if it should be generated randomly
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(500)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-4)`: a functor indicating that the stopping criterion is fulfilled
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `velocity`:                  a set of tangent vectors (of type `AbstractVector{T}`) representing the velocities of the particles, per default a random tangent vector per initial position

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively. If you provide the objective directly, these decorations can still be specified

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
