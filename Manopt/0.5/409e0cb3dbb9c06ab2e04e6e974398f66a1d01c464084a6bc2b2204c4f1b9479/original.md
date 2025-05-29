```
NonmonotoneLinesearch(; kwargs...)
NonmonotoneLinesearch(M::AbstractManifold; kwargs...)
```

A functor representing a nonmonotone line search using the Barzilai-Borwein step size [IannazzoPorcelli:2017](@cite).

This method first computes

(x -> p, F-> f)

$$
y_{k} = \operatorname{grad}f(p_{k}) - \mathcal T_{p_k←p_{k-1}}\operatorname{grad}f(p_{k-1})
$$

and

$$
s_{k} = - α_{k-1} ⋅ \mathcal T_{p_k←p_{k-1}}\operatorname{grad}f(p_{k-1}),
$$

where $α_{k-1}$ is the step size computed in the last iteration and $\mathcal T_{⋅←⋅}$ is a vector transport. Then the Barzilai—Borwein step size is

$$
α_k^{\text{BB}} = \begin{cases}   \min(α_{\text{max}}, \max(α_{\text{min}}, τ_{k})), & \text{if} ⟨s_{k}, y_{k}⟩_{p_k} > 0,\\\\    α_{\text{max}}, & \text{else,}\end{cases}
$$

where

$$
τ_{k} = \frac{⟨s_{k}, s_{k}⟩_{p_k}}{⟨s_{k}, y_{k}⟩_{p_k}},
$$

if the direct strategy is chosen, or

$$
τ_{k} =  \frac{⟨s_{k}, y_{k}⟩_{p_k}}{⟨y_{k}, y_{k}⟩_{p_k}},
$$

in case of the inverse strategy or an alternation between the two in cases for the alternating strategy. Then find the smallest $h = 0, 1, 2, …$ such that

$$
f(\operatorname{retr}_{p_k}(- σ^h α_k^{\text{BB}} \operatorname{grad}f(p_k)))  ≤
\max_{1 ≤ j ≤ \max(k+1,m)} f(p_{k+1-j}) - γ σ^h α_k^{\text{BB}} ⟨\operatorname{grad}F(p_k), \operatorname{grad}F(p_k)⟩_{p_k},
$$

where $σ ∈ (0,1)$ is a step length reduction factor , $m$ is the number of iterations after which the function value has to be lower than the current one and $γ ∈ (0,1)$ is the sufficient decrease parameter. Finally the step size is computed as

$$
α_k = σ^h α_k^{\text{BB}}.
$$

# Keyword arguments

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to store an interim result
  * `p=allocate_result(M, rand)`: to store an interim result
  * `initial_stepsize=1.0`: the step size to start the search with
  * `memory_size=10`: number of iterations after which the cost value needs to be lower than the current one
  * `bb_min_stepsize=1e-3`: lower bound for the Barzilai-Borwein step size greater than zero
  * `bb_max_stepsize=1e3`: upper bound for the Barzilai-Borwein step size greater than min_stepsize
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `strategy=direct`: defines if the new step size is computed using the `:direct`, `:indirect` or `:alternating` strategy
  * `storage=`[`StoreStateAction`](@ref)`(M; store_fields=[:Iterate, :Gradient])`: increase efficiency by using a [`StoreStateAction`](@ref) for `:Iterate` and `:Gradient`.
  * `stepsize_reduction=0.5`:  step size reduction factor contained in the interval $(0,1)$
  * `sufficient_decrease=1e-4`: sufficient decrease parameter contained in the interval $(0,1)$
  * `stop_when_stepsize_less=0.0`: smallest stepsize when to stop (the last one before is taken)
  * `stop_when_stepsize_exceeds=`[`max_stepsize`](@ref)`(M, p)`): largest stepsize when to stop to avoid leaving the injectivity radius
  * `stop_increasing_at_step=100`:  last step to increase the stepsize (phase 1),
  * `stop_decreasing_at_step=1000`: last step size to decrease the stepsize (phase 2),
