```
sosbuildsequence(s::AbstractSwitchedSystem, d::Integer;
                 v_0=:Random, p_0=:Random, l::Integer=1,
                 Δt::Float64=1., niter::Integer=42,
                 kws...)
```

Compute the truncation of length `l` of the high growth rate infinite sequence produced by the algorithm introduced in [LJP17]. The trajectory ends at mode `v_0` (or a random one if `v_0` is `:Random`) and is built backward as explained in [LJP17]. The measures used to guide the construction are the infeasibility certificates of highest growth rate computed by [`soslyap`](@ref) with polynomials of degree `2d`. The starting polynomial is either `p_0`, or a random strictly sum-of-squares polynomial if `p_0` is `:Random` or the primal solution of [`soslyap`](@ref) certifying the best upper bound for mode `v_0`.

  * [LJP17] B. Legat, R. M. Jungers, and P. A. Parrilo.

[Certifying unstability of Switched Systems using Sum of Squares Programming](https://arxiv.org/abs/1710.01814), arXiv preprint arXiv:1710.01814, **2017**.
