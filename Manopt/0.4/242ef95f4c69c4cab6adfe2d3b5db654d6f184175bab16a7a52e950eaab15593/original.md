```
NonmonotoneLinesearch <: Linesearch
```

A functor representing a nonmonotone line search using the Barzilai-Borwein step size [IannazzoPorcelli:2017](@cite). Together with a gradient descent algorithm this line search represents the Riemannian Barzilai-Borwein with nonmonotone line-search (RBBNMLS) algorithm. The order is shifted in comparison of the algorithm steps from the paper by Iannazzo and Porcelli so that in each iteration this line search first finds

$$
y_{k} = \operatorname{grad}F(x_{k}) - \operatorname{T}_{x_{k-1} → x_k}(\operatorname{grad}F(x_{k-1}))
$$

and

$$
s_{k} = - α_{k-1} * \operatorname{T}_{x_{k-1} → x_k}(\operatorname{grad}F(x_{k-1})),
$$

where $α_{k-1}$ is the step size computed in the last iteration and $\operatorname{T}$ is a vector transport. Then the Barzilai—Borwein step size is

$$
α_k^{\text{BB}} = \begin{cases}
\min(α_{\text{max}}, \max(α_{\text{min}}, τ_{k})),  & \text{if } ⟨s_{k}, y_{k}⟩_{x_k} > 0,\\
α_{\text{max}}, & \text{else,}
\end{cases}
$$

where

$$
τ_{k} = \frac{⟨s_{k}, s_{k}⟩_{x_k}}{⟨s_{k}, y_{k}⟩_{x_k}},
$$

if the direct strategy is chosen,

$$
τ_{k} = \frac{⟨s_{k}, y_{k}⟩_{x_k}}{⟨y_{k}, y_{k}⟩_{x_k}},
$$

in case of the inverse strategy and an alternation between the two in case of the alternating strategy. Then find the smallest $h = 0, 1, 2, …$ such that

$$
F(\operatorname{retr}_{x_k}(- σ^h α_k^{\text{BB}} \operatorname{grad}F(x_k)))
\leq
\max_{1 ≤ j ≤ \min(k+1,m)} F(x_{k+1-j}) - γ σ^h α_k^{\text{BB}} ⟨\operatorname{grad}F(x_k), \operatorname{grad}F(x_k)⟩_{x_k},
$$

where $σ$ is a step length reduction factor $∈ (0,1)$, $m$ is the number of iterations after which the function value has to be lower than the current one and $γ$ is the sufficient decrease parameter $∈(0,1)$. Then find the new stepsize by

$$
α_k = σ^h α_k^{\text{BB}}.
$$

# Fields

  * `initial_stepsize`:        (`1.0`) the step size to start the search with
  * `memory_size`:             (`10`) number of iterations after which the cost value needs to be lower than the current one
  * `bb_min_stepsize`:         (`1e-3`) lower bound for the Barzilai-Borwein step size greater than zero
  * `bb_max_stepsize`:         (`1e3`) upper bound for the Barzilai-Borwein step size greater than min_stepsize
  * `retraction_method`:       (`ExponentialRetraction()`) the retraction to use
  * `strategy`:                (`direct`) defines if the new step size is computed using the direct, indirect or alternating strategy
  * `storage`:                 (for `:Iterate` and `:Gradient`) a [`StoreStateAction`](@ref)
  * `stepsize_reduction`:      (`0.5`) step size reduction factor contained in the interval (0,1)
  * `sufficient_decrease`:     (`1e-4`) sufficient decrease parameter contained in the interval (0,1)
  * `vector_transport_method`: (`ParallelTransport()`) the vector transport method to use

as well as for internal use

  * `candidate_point`:           (`allocate_result(M, rand)`) to store an interim result

Furthermore the following fields act as safeguards

  * `stop_when_stepsize_less:     (`0.0`) smallest stepsize when to stop (the last one before is taken)
  * `stop_when_stepsize_exceeds`: ([`max_stepsize`](@ref)`(M, p)`) largest stepsize when to stop.
  * `stop_increasing_at_step`:    (^100`) last step to increase the stepsize (phase 1),
  * `stop_decreasing_at_step`:    (`1000`) last step size to decrease the stepsize (phase 2),

Pass `:Messages` to a `debug=` to see `@info`s when these happen.

# Constructor

```
NonmonotoneLinesearch()
```

with the fields their order as optional arguments (deprecated). THis is deprecated, since both defaults and the memory allocation for the candidate do not take into account which manifold the line search operates on.

```
NonmonotoneLinesearch(M)
```

with the fields as keyword arguments and where the retraction and vector transport are set to the default ones on `M`, respectively.

The constructors return the functor to perform nonmonotone line search.
