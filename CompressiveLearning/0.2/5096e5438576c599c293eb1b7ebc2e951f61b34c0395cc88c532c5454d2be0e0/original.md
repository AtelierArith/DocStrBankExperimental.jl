```julia
CLOMPR(
    s,
    k,
    prmType,
    A;
    replacement,
    weights_update_method,
    weights_update,
    bound_alpha,
    init_method,
    init_bounds,
    init_extra_params,
    maxits_inloop,
    maxits_final,
    bounds,
    bestatom_inits,
    bestatom_inits_replacement,
    save_history,
    out_dic
)

```

CL-OMP(R) algorithm. Returns a pair `(θ, α)` of parameters and weights ideally minimizing `‖Sketch(θ,α)-s‖₂`, where the sketch is computed according to `A`. where `θ` is a `prmtype.p` × `k` matrix of parameters, and `α` the length-`k` vector of associated weights.

Optional parameters:

  * `replacement`: the number of iterations is set to `2k` instade of `k`. After the `k`th iteration, optimization is performed over `k`+1 atoms and the best `k` are keeped.
  * `init_method`: method for picking a new atom (default: :uniform, :randn, :atzero). Option :uniform requires bounds to be provided. Supported arguments might change with the type of the parameters.
  * `maxits_inloop`: maximum number of iterations for the global optimization inside the main loop (Int, default: `300`).
  * `maxits_final`: maximum number of iterations for the last global optimization (Int, default: `3000`).
  * `bounds`: tuple of lower bound, upper bound (default: `(-Inf,Inf)`) for the optimization parameters. Each bound can be a scalar or a vector of a dimension coherent with the `prmtype` provided. Note that when the optimization parameters correspond to multiple variables (e.g. μ and σ for GMMs), it is advised to use vector bounds as automatic vectorization might be meaningless.
  * `init_bounds`: bounds used when looking for a new atom. If none are provided, `bounds` will be used as well for initialization.
  * `bestatom_inits`: Number of initialization trials (best one is keeped) when picking a new atom in the first `k` steps (Int, default: `3`).
  * `bestatom_inits_replacement`: Number of initialization trials (best one is keeped) when picking a new atom in the replacement steps (Int, default: `10`).
  * `save_history`: Bool (default: `false`), requires `out_dic` to be provided.
  * `out_dic`: Dict (default: nothing). When provided, informations about the algorithm will be stored in this dictionnary.
  * `weights_update`: should be any of `:always, :onceperit, :attheend (default), :never`
  * `weights_update_method`: should be any of `:normalize, :project (default)`, where `:project` means projection on the simplex.
