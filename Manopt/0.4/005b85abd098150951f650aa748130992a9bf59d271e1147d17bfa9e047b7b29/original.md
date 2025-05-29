```
patricle_swarm(M, f; kwargs...)
patricle_swarm(M, f, swarm; kwargs...)
patricle_swarm(M, mco::AbstractManifoldCostObjective; kwargs..)
patricle_swarm(M, mco::AbstractManifoldCostObjective, swarm; kwargs..)
```

perform the particle swarm optimization algorithm (PSO), starting with an initial `swarm` [BorckmansIshtevaAbsil:2010](@cite). If no `swarm` is provided, `swarm_size` many random points are used.

The aim of PSO is to find the particle position $p$ on the `Manifold M` that solves approximately

$$
\min_{p ∈\mathcal{M}} F(p).
$$

To this end, a swarm $S = \{s_1, \ldots, s_n\}$ of particles is moved around the manifold `M` in the following manner. For every particle $s_k^{(i)}$ the new particle velocities $X_k^{(i)}$ are computed in every step $i$ of the algorithm by

$$
  X_k^{(i)} = ω \, \operatorname{T}_{s_k^{(i)}\gets s_k^{(i-1)}}X_k^{(i-1)} + c r_1  \operatorname{retr}_{s_k^{(i)}}^{-1}(p_k^{(i)}) + s r_2 \operatorname{retr}_{s_k^{(i)}}^{-1}(p),
$$

where

  * $s_k^{(i)}$ is the current particle position,
  * $ω$ denotes the inertia,
  * $c$ and $s$ are a cognitive and a social weight, respectively,
  * $r_j$, $j=1,2$ are random factors which are computed new for each particle and step
  * $T$ denotes the vector transport and $\operatorname{retr}^{-1}$ the inverse retraction used

Then the position of the particle is updated as

$$
s_k^{(i+1)} = \operatorname{retr}_{s_k^{(i)}}(X_k^{(i)}),
$$

where $\operatorname{retr}$ denotes a retraction on the `Manifold` `M`. Then the single particles best entries $p_k^{(i)}$ are updated as

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

  * `M`:     a manifold $\mathcal M$
  * `f`:     a cost function $F:\mathcal M→ℝ$ to minimize
  * `swarm`: (`[rand(M) for _ in 1:swarm_size]`) an initial swarm of points.

Instead of a cost function `f` you can also provide an [`AbstractManifoldCostObjective`](@ref) `mco`.

# Optional

  * `cognitive_weight`:          (`1.4`) a cognitive weight factor
  * `inertia`:                   (`0.65`) the inertia of the particles
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M, eltype(swarm))`) an inverse retraction to use.
  * `swarm_size`:                (`100`) swarm size, if it should be generated randomly
  * `retraction_method`:         (`default_retraction_method(M, eltype(swarm))`) a retraction to use.
  * `social_weight`:             (`1.4`) a social weight factor
  * `stopping_criterion`:        ([`StopAfterIteration`](@ref)`(500) |`[`StopWhenChangeLess`](@ref)`(1e-4)`) a functor inheriting from [`StoppingCriterion`](@ref) indicating when to stop.
  * `vector_transport_method`:   (`default_vector_transport_method(M, eltype(swarm))`) a vector transport method to use.
  * `velocity`:                  a set of tangent vectors (of type `AbstractVector{T}`) representing the velocities of the particles, per default a random tangent vector per initial position

All other keyword arguments are passed to [`decorate_state!`](@ref) for decorators or [`decorate_objective!`](@ref), respectively. If you provide the [`ManifoldGradientObjective`](@ref) directly, these decorations can still be specified

# Output

the obtained (approximate) minimizer $g$, see [`get_solver_return`](@ref) for details
