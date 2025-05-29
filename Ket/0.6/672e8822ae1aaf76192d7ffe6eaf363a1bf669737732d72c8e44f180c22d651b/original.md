```
function ppt_mixture(
    ρ::AbstractMatrix{T},
    dims::AbstractVecOrTuple,
    obs::AbstractVector{<:AbstractMatrix} = Vector{Matrix}();
    verbose::Bool = false,
    solver = Hypatia.Optimizer{_solver_type(T)})
```

Lower bound on the white noise such that ρ is still a genuinely multipartite entangled state that can be detected with a witness using only the operators provided in `obs`, and the values of the coefficients defining such a witness.

More precisely, if a list of observables $O_i$ is provided in the parameter `obs`, the witness will be of the form $∑_i α_i O_i$ and detects ρ only using these observables. For example, using only two-body operators (and lower order) one can call

```julia-repl
julia> two_body_basis = collect(Iterators.flatten(n_body_basis(i, 3) for i ∈ 0:2))
julia> ppt_mixture(state_ghz(2, 3), [2, 2, 2], two_body_basis)
```

Reference: Jungnitsch, Moroder, Gühne [arXiv:quant-ph/0401118](https://arxiv.org/abs/quant-ph/0401118)
