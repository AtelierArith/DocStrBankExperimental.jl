```
ChambollePockState <: AbstractPrimalDualSolverState
```

stores all options and variables within a linearized or exact Chambolle Pock. The following list provides the order for the constructor, where the previous iterates are initialized automatically and values with a default may be left out.

  * `m`:                              base point on $\mathcal M$
  * `n`:                              base point on $\mathcal N$
  * `p`:                              an initial point on $x^{(0)} ∈\mathcal M$ (and its previous iterate)
  * `X`:                              an initial tangent vector $X^{(0)}∈T^*\mathcal N$ (and its previous iterate)
  * `pbar`:                           the relaxed iterate used in the next dual update step (when using `:primal` relaxation)
  * `Xbar`:                           the relaxed iterate used in the next primal update step (when using `:dual` relaxation)
  * `primal_stepsize`:                (`1/sqrt(8)`) proximal parameter of the primal prox
  * `dual_stepsize`:                  (`1/sqrt(8)`) proximal parameter of the dual prox
  * `acceleration`:                   (`0.`) acceleration factor due to Chambolle & Pock
  * `relaxation`:                     (`1.`) relaxation in the primal relaxation step (to compute `pbar`)
  * `relax`:                          (`:primal`) which variable to relax (`:primal` or `:dual`)
  * `stop`:                           a [`StoppingCriterion`](@ref)
  * `variant`:                        (`exact`) whether to perform an `:exact` or `:linearized` Chambolle-Pock
  * `update_primal_base`:             (`(p,o,i) -> o.m`) function to update the primal base
  * `update_dual_base`:               (`(p,o,i) -> o.n`) function to update the dual base
  * `retraction_method`:              (`default_retraction_method(M, typeof(p))`) the retraction to use
  * `inverse_retraction_method`:      (`default_inverse_retraction_method(M, typeof(p))`) an inverse retraction to use on the manifold $\mathcal M$.
  * `inverse_retraction_method_dual`: (`default_inverse_retraction_method(N, typeof(n))`) an inverse retraction to use on manifold $\mathcal N$.
  * `vector_transport_method`:        (`default_vector_transport_method(M, typeof(p))`) a vector transport to use on the manifold $\mathcal M$.
  * `vector_transport_method_dual`:   (`default_vector_transport_method(N, typeof(n))`) a vector transport to use on manifold $\mathcal N$.

where for the last two the functions a [`AbstractManoptProblem`](@ref)`p`, [`AbstractManoptSolverState`](@ref)`o` and the current iterate `i` are the arguments. If you activate these to be different from the default identity, you have to provide `p.Λ` for the algorithm to work (which might be `missing` in the linearized case).

# Constructor

```
ChambollePockState(M::AbstractManifold, N::AbstractManifold,
    m::P, n::Q, p::P, X::T, primal_stepsize::Float64, dual_stepsize::Float64;
    kwargs...
)
```

where all other fields are keyword arguments with their default values given in brackets.

if `Manifolds.jl` is loaded, `N` is also a keyword argument and set to `TangentBundle(M)` by default.
