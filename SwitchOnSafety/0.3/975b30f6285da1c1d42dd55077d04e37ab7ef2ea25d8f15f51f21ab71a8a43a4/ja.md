```
sosbuildsequence(s::AbstractSwitchedSystem, d::Integer;
                 v_0=:Random, p_0=:Random, l::Integer=1,
                 Δt::Float64=1., niter::Integer=42,
                 kws...)
```

高成長率の無限列の長さ `l` の切り捨てを計算します。この列は、[LJP17] で紹介されたアルゴリズムによって生成されます。軌道はモード `v_0`（または `v_0` が `:Random` の場合はランダムなもの）で終了し、[LJP17] で説明されているように逆方向に構築されます。構築を導くために使用される測度は、[`soslyap`](@ref) によって計算された最高成長率の不適合証明書であり、次数 `2d` の多項式を使用します。開始多項式は `p_0` であるか、`p_0` が `:Random` の場合はランダムな厳密な和の平方多項式、またはモード `v_0` のための最良の上限を証明する [`soslyap`](@ref) の原始解です。

  * [LJP17] B. Legat, R. M. Jungers, and P. A. Parrilo.

[Certifying unstability of Switched Systems using Sum of Squares Programming](https://arxiv.org/abs/1710.01814), arXiv preprint arXiv:1710.01814, **2017**.
