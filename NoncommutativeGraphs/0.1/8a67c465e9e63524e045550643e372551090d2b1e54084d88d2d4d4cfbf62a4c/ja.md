```julia
dsw(
    g::NoncommutativeGraphs.S0Graph,
    w::AbstractMatrix{<:Number};
    use_diag_optimization,
    eps,
    verbose
) -> NamedTuple{(:λ, :x, :Z), <:Tuple{Any, Any, Any}}

```

重み付きθをarxiv:2101.00162の定理14を使用して計算します。

最適なλ、x、およびZの値を名前付きタプルで返します。`use_diag_optimization=true`（デフォルト）であれば、`x ⪰ w`であり、`x`はS₀の共役にあります。arxiv:2101.00162の定理29によれば、θ(g, w) = θ(g, x)です。
