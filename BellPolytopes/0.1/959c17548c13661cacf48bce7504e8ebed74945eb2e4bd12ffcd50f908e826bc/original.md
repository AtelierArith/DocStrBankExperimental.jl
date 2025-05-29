Calls the lazy pairwise blended conditional gradient algorithm from Frank-Wolfe package.

Arguments:

  * `p`: a correlation/probability tensor of order `N`.

Returns:

  * `x`: a correlation/probability tensor of order `N`, the output of the Frank-Wolfe algorithm,
  * `ds`: a deterministic strategy, the atom returned by the last LMO,
  * `primal`: `½|x-v₀*p|²`,
  * `dual_gap`: `⟨x-v₀*p, x-ds⟩`,
  * `active_set`: all deterministic strategies used for the decomposition of the last iterate `x`, contains fields `weights`, `atoms`, and `x`,
  * `M`: a Bell inequality, meaningful only if the dual gap is small enough,
  * `β`: the local bound of the inequality parametrised by `M`, reliable only if the last LMO is exact.

Optional arguments:

  * `prob`: a boolean, indicates if `p` is a corelation or probability array,
  * `marg`: a boolean, indicates if `p` contains marginals,
  * `v0`: the visibility used to make a nonlocal `p` closer to the local polytope,
  * `epsilon`: the tolerance, used as a stopping criterion (when the primal value or the dual gap go below its value), by default 1e-7,
  * `verbose`: an integer, indicates the level of verbosity from 0 to 3,
  * `shr2`: the potential underlying shrinking factor, used to display the lower bound in the callback,
  * `mode`: an integer, 0 is for the heuristic LMO, 1 for the enumeration LMO,
  * `nb`: an integer, number of random tries in the LMO, if heuristic, by default 10^2,
  * `TL`: type of the last call of the LMO,
  * `mode_last`: an integer, mode of the last call of the LMO, -1 for no last call,
  * `nb_last`: an integer, number of random tries in the last LMO, if heuristic, by default 10^5,
  * `sym`: a boolean, indicates if the symmetry of the input should be used, by default automatic choice,
  * `use_array`: a boolean, indicates to store the full deterministic strategies to trade memory for speed in multipartite scenarios,
  * `callback_interval`: an integer, print interval if `verbose` = 3,
  * `seed`: an integer, the initial random seed.
