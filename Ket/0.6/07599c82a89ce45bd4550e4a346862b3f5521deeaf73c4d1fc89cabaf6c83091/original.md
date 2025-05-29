```
seesaw(
    CG::Matrix,
    scenario::AbstractVecOrTuple,
    d::Integer,
    n_trials::Integer = 1;
    verbose::Bool = false,
    solver = Hypatia.Optimizer{_solver_type(T)})
```

Maximizes bipartite Bell functional in Collins-Gisin notation `CG` using the seesaw heuristic. `scenario` is a vector detailing the number of inputs and outputs, in the order [oa, ob, ia, ib]. `d` is an integer determining the local dimension of the strategy.

If `oa` = `ob` = 2 the heuristic reduces to a bunch of eigenvalue problems. Otherwise semidefinite programming is needed and we use the assemblage version of seesaw.

The heuristic is run `n_trials` times, and the best run is outputted.

References:

  * Pál and Vértesi, [arXiv:1006.3032](https://arxiv.org/abs/1006.3032)
  * Tavakoli et al., [arXiv:2307.02551](https://arxiv.org/abs/2307.02551) (Sec. II.B.1)
