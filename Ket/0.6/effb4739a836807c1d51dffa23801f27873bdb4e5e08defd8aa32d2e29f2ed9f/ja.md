```
function ppt_mixture(
    ρ::AbstractMatrix{T},
    dims::AbstractVecOrTuple;
    verbose::Bool = false,
    solver = Hypatia.Optimizer{_solver_type(T)})
```

ρが真に多体エンタングル状態であり、ρを検出するGMEウィットネスであるためのホワイトノイズの下限。

GME状態の集合はPPT混合の集合によって近似されるため、二分割におけるエンタングルメントはPPT基準によって決定されます。状態がPPT混合である場合、ウィットネスの代わりに0行列を返します。

参考文献: Jungnitsch, Moroder, Gühne, [arXiv:quant-ph/0401118](https://arxiv.org/abs/quant-ph/0401118)
