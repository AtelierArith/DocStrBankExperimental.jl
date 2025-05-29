```julia
continuation(
    prob,
    algdc,
    contParams;
    verbosity,
    plot,
    linear_algo,
    dot_palc,
    callback_newton,
    filename,
    normC,
    kwcont...
)

```

This function computes the set of curves of solutions `γ(s) = (x(s), p(s))` to the equation `F(x,p) = 0` based on the algorithm of **deflated continuation** as described in Farrell, Patrick E., Casper H. L. Beentjes, and Ásgeir Birkisson. “The Computation of Disconnected Bifurcation Diagrams.” ArXiv:1603.00809 [Math], March 2, 2016. http://arxiv.org/abs/1603.00809.

Depending on the options in `contParams`, it can locate the bifurcation points on each branch. Note that you can specify different predictors using `alg`.

# Arguments:

  * `prob::AbstractBifurcationProblem` bifurcation problem
  * `alg::DefCont`, deflated continuation algorithm, see [`DefCont`](@ref)
  * `contParams` parameters for continuation. See [`ContinuationPar`](@ref) for more information about the options

# Optional Arguments:

  * `plot = false` whether to plot the solution while computing,
  * `callback_newton` callback for newton iterations. see docs for `newton`. Can be used to change preconditioners or affect the newton iterations. In the deflation part of the algorithm, when seeking for new branches, the callback is passed the keyword argument `fromDeflatedNewton = true` to tell the user can it is not in the continuation part (regular newton) of the algorithm,
  * `verbosity::Int` controls the amount of information printed during the continuation process. Must belong to `{0,⋯,5}`,
  * `normC = norm` norm used in the Newton solves,
  * `dot_palc = (x, y) -> dot(x, y) / length(x)`, dot product used to define the weighted dot product (resp. norm) $\|(x, p)\|^2_\theta$ in the constraint $N(x, p)$ (see online docs on [PALC](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/PALC/)). This argument can be used to remove the factor `1/length(x)` for example in problems where the dimension of the state space changes (mesh adaptation, ...),

# Outputs:

  * `contres::DCResult` composite type which contains the computed branches. See [`ContResult`](@ref) for more information,
