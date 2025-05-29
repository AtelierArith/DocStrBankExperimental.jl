# OrdinaryDiffEq.jl

[![Join the chat at https://julialang.zulipchat.com #sciml-bridged](https://img.shields.io/static/v1?label=Zulip&message=chat&color=9558b2&labelColor=389826)](https://julialang.zulipchat.com/#narrow/stream/279055-sciml-bridged) [![Global Docs](https://img.shields.io/badge/docs-SciML-blue.svg)](https://docs.sciml.ai/OrdinaryDiffEq/stable/)

[![codecov](https://codecov.io/gh/SciML/OrdinaryDiffEq.jl/branch/master/graph/badge.svg)](https://app.codecov.io/gh/SciML/OrdinaryDiffEq.jl) [![Build Status](https://github.com/SciML/OrdinaryDiffEq.jl/workflows/CI/badge.svg)](https://github.com/SciML/OrdinaryDiffEq.jl/actions?query=workflow%3ACI) [![Build status](https://badge.buildkite.com/5f39777d009ce94ef1dcf2a4881c68b9fbcaf6f69f1d8b8df2.svg?branch=master)](https://buildkite.com/julialang/ordinarydiffeq-dot-jl)

[![ColPrac: Contributor's Guide on Collaborative Practices for Community Packages](https://img.shields.io/badge/ColPrac-Contributor%27s%20Guide-blueviolet)](https://github.com/SciML/ColPrac) [![SciML Code Style](https://img.shields.io/static/v1?label=code%20style&message=SciML&color=9558b2&labelColor=389826)](https://github.com/SciML/SciMLStyle)

OrdinaryDiffEq.jlは、DifferentialEquationsエコシステムのコンポーネントパッケージです。これは常微分方程式のソルバーとユーティリティを保持しています。完全に独立しており、単独で使用できますが、この機能を使用したいユーザーは、[DifferentialEquations.jl](https://github.com/SciML/DifferentialEquations.jl)を確認する必要があります。

## インストール

Juliaが正しくインストールされていると仮定すると、OrdinaryDiffEq.jlを標準的な方法でインポートするだけで済みます：

```julia
import Pkg;
Pkg.add("OrdinaryDiffEq");
```

## API

OrdinaryDiffEq.jlはSciML共通インターフェースの一部ですが、DifferentialEquations.jlとは独立して使用できます。唯一の要件は、ユーザーが`solve`にOrdinaryDiffEq.jlアルゴリズムを渡すことです。たとえば、`Tsit5()`アルゴリズムを使用して、[ドキュメントのODEチュートリアル](https://docs.sciml.ai/DiffEqDocs/stable/getting_started/#ode_example)を解くことができます：

```julia
using OrdinaryDiffEq
f(u, p, t) = 1.01 * u
u0 = 1 / 2
tspan = (0.0, 1.0)
prob = ODEProblem(f, u0, tspan)
sol = solve(prob, Tsit5(), reltol = 1e-8, abstol = 1e-8)
using Plots
plot(sol, linewidth = 5, title = "Solution to the linear ODE with a thick line",
    xaxis = "Time (t)", yaxis = "u(t) (in μm)", label = "My Thick Line!") # legend=false
plot!(sol.t, t -> 0.5 * exp(1.01t), lw = 3, ls = :dash, label = "True Solution!")
```

その例では、`f(u,p,t)`のアウトオブプレース構文を使用していますが、インプレース構文（方程式系に対してより効率的）はローレンツの例で示されています：

```julia
using OrdinaryDiffEq
function lorenz!(du, u, p, t)
    du[1] = 10.0(u[2] - u[1])
    du[2] = u[1] * (28.0 - u[3]) - u[2]
    du[3] = u[1] * u[2] - (8 / 3) * u[3]
end
u0 = [1.0; 0.0; 0.0]
tspan = (0.0, 100.0)
prob = ODEProblem(lorenz!, u0, tspan)
sol = solve(prob, Tsit5())
using Plots;
plot(sol, idxs = (1, 2, 3))
```

非常に高速な静的配列バージョンは、モデルのサイズに特化してコンパイルできます。たとえば：

```julia
using OrdinaryDiffEq, StaticArrays
function lorenz(u, p, t)
    SA[10.0(u[2] - u[1]), u[1] * (28.0 - u[3]) - u[2], u[1] * u[2] - (8 / 3) * u[3]]
end
u0 = SA[1.0; 0.0; 0.0]
tspan = (0.0, 100.0)
prob = ODEProblem(lorenz, u0, tspan)
sol = solve(prob, Tsit5())
```

「洗練されたODE」、例えば動的方程式や`SecondOrderODEProblem`については、[DiffEqDocs](https://diffeq.sciml.ai/dev/types/ode_types/)を参照してください。たとえば、[DiffEqTutorials.jl](https://github.com/SciML/DiffEqTutorials.jl)では、シンプレクティック法を使用して運動方程式を解く方法を示しています：

```julia
function HH_acceleration!(dv, v, u, p, t)
    x, y = u
    dx, dy = dv
    dv[1] = -x - 2x * y
    dv[2] = y^2 - y - x^2
end
initial_positions = [0.0, 0.1]
initial_velocities = [0.5, 0.0]
prob = SecondOrderODEProblem(HH_acceleration!, initial_velocities, initial_positions, tspan)
sol2 = solve(prob, KahanLi8(), dt = 1 / 10);
```

他の洗練された形式にはIMEXおよび半線形ODE（指数積分器用）があります。

## 利用可能なソルバー

利用可能なソルバーのリストについては、[DifferentialEquations.jl ODE Solvers](https://diffeq.sciml.ai/dev/solvers/ode_solve/)、[Dynamical ODE Solvers](http://diffeq.sciml.ai/dev/solvers/dynamical_solve/)、および[Split ODE Solvers](http://diffeq.sciml.ai/dev/solvers/split_ode_solve/)のページを参照してください。
