```
function ppt_mixture(
    ρ::AbstractMatrix{T},
    dims::AbstractVecOrTuple,
    obs::AbstractVector{<:AbstractMatrix} = Vector{Matrix}();
    verbose::Bool = false,
    solver = Hypatia.Optimizer{_solver_type(T)})
```

ρが依然として真の多体エンタングル状態であり、`obs`で提供された演算子のみを使用してウィットネスで検出できるようにするためのホワイトノイズの下限。

より正確には、パラメータ`obs`に観測量のリスト$O_i$が提供されると、ウィットネスは$∑_i α_i O_i$の形になり、これらの観測量のみを使用してρを検出します。たとえば、二体演算子（およびそれ以下の次数）のみを使用して、次のように呼び出すことができます。

```julia-repl
julia> two_body_basis = collect(Iterators.flatten(n_body_basis(i, 3) for i ∈ 0:2))
julia> ppt_mixture(state_ghz(2, 3), [2, 2, 2], two_body_basis)
```

参考文献: Jungnitsch, Moroder, Gühne [arXiv:quant-ph/0401118](https://arxiv.org/abs/quant-ph/0401118)
