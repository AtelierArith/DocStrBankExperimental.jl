boltzmann(eq::DiffusionEquation) -> DifferentialEquations.ODEFunction

`eq`をボルツマン変数`o`に基づいて定義された常微分方程式（ODE）に変換します。

独立変数`o`と2つの成分を持つODEを返します。最初の成分は解自体であり、2番目の成分は解の`o`-導関数です。このODEは、`StaticArrays.SVector`に格納された成分に最適化されています。

参照: [`DifferentialEquations`](https://diffeq.sciml.ai/stable/), [`StaticArrays.SVector`](https://juliaarrays.github.io/StaticArrays.jl/stable/pages/api/#SVector-1)
