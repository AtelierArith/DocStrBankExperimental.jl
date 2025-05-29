```
NelderMead(M::AbstractManifold, f, population=NelderMeadSimplex(M))
NelderMead(M::AbstractManifold, mco::AbstractManifoldCostObjective, population=NelderMeadSimplex(M))
NelderMead!(M::AbstractManifold, f, population)
NelderMead!(M::AbstractManifold, mco::AbstractManifoldCostObjective, population)
```

Solve a Nelder-Mead minimization problem for the cost function $f: \mathcal M → ℝ$ on the manifold `M`. If the initial [`NelderMeadSimplex`](@ref) is not provided, a random set of points is chosen. The compuation can be performed in-place of the `population`.

The algorithm consists of the following steps. Let $d$ denote the dimension of the manifold $\mathcal M$.

1. Order the simplex vertices $p_i, i=1,…,d+1$ by increasing cost, such that we have $f(p_1) ≤ f(p_2) ≤ … ≤ f(p_{d+1})$.
2. Compute the Riemannian center of mass [Karcher:1977](@cite), cf. [`mean`](@extref Statistics.mean-Tuple{AbstractManifold, Vararg{Any}}), $p_{\text{m}}$  of the simplex vertices $p_1,…,p_{d+1}$.
3. Reflect the point with the worst point at the mean $p_{\text{r}} = \operatorname{retr}_{p_{\text{m}}}\bigl( - α\operatorname{retr}^{-1}_{p_{\text{m}}} (p_{d+1}) \bigr)$  If $f(p_1) ≤ f(p_{\text{r}}) ≤ f(p_{d})$ then set $p_{d+1} = p_{\text{r}}$ and go to step 1.
4. Expand the simplex if $f(p_{\text{r}}) < f(p_1)$ by computing the expantion point $p_{\text{e}} = \operatorname{retr}_{p_{\text{m}}}\bigl( - γα\operatorname{retr}^{-1}_{p_{\text{m}}} (p_{d+1}) \bigr)$,  which in this formulation allows to reuse the tangent vector from the inverse retraction from before.  If $f(p_{\text{e}}) < f(p_{\text{r}})$ then set $p_{d+1} = p_{\text{e}}$ otherwise set set $p_{d+1} = p_{\text{r}}$. Then go to Step 1.
5. Contract the simplex if $f(p_{\text{r}}) ≥ f(p_d)$.

    1. If $f(p_{\text{r}}) < f(p_{d+1})$ set the step $s = -ρ$
    2. otherwise set $s=ρ$.

    Compute the contraction point $p_{\text{c}} = \operatorname{retr}_{p_{\text{m}}}\bigl(s\operatorname{retr}^{-1}_{p_{\text{m}}} p_{d+1} \bigr)$.

    1. in this case if $f(p_{\text{c}}) < f(p_{\text{r}})$ set $p_{d+1} = p_{\text{c}}$ and go to step 1
    2. in this case if $f(p_{\text{c}}) < f(p_{d+1})$ set $p_{d+1} = p_{\text{c}}$ and go to step 1
6. Shrink all points (closer to $p_1$). For all $i=2,...,d+1$ set  $p_{i} = \operatorname{retr}_{p_{1}}\bigl( σ\operatorname{retr}^{-1}_{p_{1}} p_{i} \bigr).$

For more details, see The Euclidean variant in the Wikipedia [https://en.wikipedia.org/wiki/Nelder-Mead_method](https://en.wikipedia.org/wiki/Nelder-Mead_method) or Algorithm 4.1 in [http://www.optimization-online.org/DB_FILE/2007/08/1742.pdf](http://www.optimization-online.org/DB_FILE/2007/08/1742.pdf).

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `population::`[`NelderMeadSimplex`](@ref)`=`[`NelderMeadSimplex`](@ref)`(M)`: an initial simplex of $d+1$ points, where $d$ is the [`manifold_dimension`](@extref `ManifoldsBase.manifold_dimension-Tuple{AbstractManifold}`) of `M`.

# Keyword arguments

  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(2000)`[`|`](@ref StopWhenAny)[`StopWhenPopulationConcentrated`](@ref)`()`): a functor indicating that the stopping criterion is fulfilled a [`StoppingCriterion`](@ref)
  * `α=1.0`: reflection parameter $α > 0$:
  * `γ=2.0` expansion parameter $γ$:
  * `ρ=1/2`: contraction parameter, $0 < ρ ≤ \frac{1}{2}$,
  * `σ=1/2`: shrink coefficient, $0 < σ ≤ 1$
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
