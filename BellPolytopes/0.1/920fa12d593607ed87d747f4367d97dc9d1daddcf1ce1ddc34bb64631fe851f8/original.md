Compute the nonlocality threshold of the qubit measurements encoded by the Bloch vectors `vec` in a Bell scenario with `N` parties.

Arguments:

  * `vec`: an `m × 3` matrix with Bloch vectors coordinates,
  * `N`: the number of parties.

Returns:

  * `lower_bound_infinite`: a lower bound on the nonlocality threshold under all projective measurements (in the subspace spanned by `vec` in the Bloch sphere),
  * `lower_bound`: a lower bound on the nonlocality threshold under the measurements provided in input,
  * `upper_bound`: a (heuristic) upper bound on the nonlocality threshold under the measurements provided in input, also valid for all projective measurements,
  * `local_model`: a decomposition of the correlation tensor obtained by applying the measurements encoded by the Bloch vectors `vec` on all `N` subsystems of the shared state `rho` with visibility `lower_bound`,
  * `bell_inequality`: a (heuristic) Bell inequality corresponding to `upper_bound`.

Optional arguments:

  * `rho`: the shared state, by default the singlet state in the bipartite case and the GHZ state otherwise,
  * `v0`: the initial visibility, which should be an upper bound on the nonlocality threshold, 1.0 by default,
  * `precision`: number of digits of `lower_bound`, 4 by default,
  * for the other optional arguments, see `bell_frank_wolfe`.
