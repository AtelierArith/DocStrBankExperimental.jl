```
function ppt_mixture(
    ρ::AbstractMatrix{T},
    dims::AbstractVecOrTuple;
    verbose::Bool = false,
    solver = Hypatia.Optimizer{_solver_type(T)})
```

Lower bound on the white noise such that ρ is still a genuinely multipartite entangled state and a GME witness that detects ρ.

The set of GME states is approximated by the set of PPT mixtures, so the entanglement across the bipartitions is decided with the PPT criterion. If the state is a PPT mixture, returns a 0 matrix instead of a witness.

Reference: Jungnitsch, Moroder, Gühne, [arXiv:quant-ph/0401118](https://arxiv.org/abs/quant-ph/0401118)
