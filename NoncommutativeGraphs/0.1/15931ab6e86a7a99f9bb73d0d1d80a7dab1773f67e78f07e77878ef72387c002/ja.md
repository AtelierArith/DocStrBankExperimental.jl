```julia
dsw_via_complement(
    g::NoncommutativeGraphs.S0Graph,
    w::AbstractMatrix{<:Number};
    use_diag_optimization,
    eps,
    verbose
) -> NamedTuple{(:λ, :x, :y, :Z), <:NTuple{4, Any}}

```

補集合グラフを使用して重み付きθを計算します。arxiv:2101.00162の定理29を使用します。

θ(S, w) = max{ tr(w x) : x ⪰ 0, y = Ψ(x), θ(Sᶜ, y) ≤ 1 }

最適なλ、x、y、およびZを名前付きタプルで返します。

wがS₀の共役にある場合、重みwとyはarxiv:2101.00162の定理32の不等式を満たします。
