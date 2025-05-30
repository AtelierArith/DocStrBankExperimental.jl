# StochasticDiffEq.jl

[![Join the chat at https://gitter.im/JuliaDiffEq/Lobby](https://badges.gitter.im/JuliaDiffEq/Lobby.svg)](https://gitter.im/JuliaDiffEq/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) [![Build Status](https://github.com/SciML/StochasticDiffEq.jl/workflows/CI/badge.svg)](https://github.com/SciML/StochasticDiffEq.jl/actions?query=workflow%3ACI) [![Build status](https://badge.buildkite.com/6fb92a51b843f3e8a3a278678fe513c86a6d0d86895847fc52.svg?branch=master)](https://buildkite.com/julialang/stochasticdiffeq-dot-jl)

StochasticDiffEq.jlは、DifferentialEquationsエコシステムのコンポーネントパッケージです。これは、確率微分方程式のソルバーとユーティリティを保持しています。完全に独立して使用可能ですが、この機能を使用したいユーザーは、[DifferentialEquations.jl](https://github.com/SciML/DifferentialEquations.jl)を確認する必要があります。

## API

StochasticDiffEq.jlは、JuliaDiffEqの共通インターフェースの一部ですが、[DifferentialEquations.jl](https://github.com/SciML/DifferentialEquations.jl)とは独立して使用できます。唯一の要件は、ユーザーが`solve`にStochasticDiffEq.jlアルゴリズムを渡すことです。たとえば、`SRIW1()`アルゴリズムを使用して、[ドキュメントのSDEチュートリアル](https://diffeq.sciml.ai/stable/tutorials/sde_example/)を解くことができます。

```julia
using StochasticDiffEq
α=1
β=1
u₀=1/2
f(u,p,t) = α*u
g(u,p,t) = β*u
dt = 1//2^(4)
tspan = (0.0,1.0)
prob = SDEProblem(f,g,u₀,(0.0,1.0))
sol =solve(prob,SRIW1())
```

`solve`のオプションは、[共通ソルバーオプションページ](https://diffeq.sciml.ai/stable/basics/common_solver_opts/)で定義されており、[ODEチュートリアル](https://diffeq.sciml.ai/stable/tutorials/ode_example/)で詳しく説明されています。

その例では、`f(u,p,t)`というアウトオブプレース構文を使用していますが、インプレース構文（方程式系に対してより効率的）は、ローレンツの例で示されています。

```julia
function lorenz(du,u,p,t)
 du[1] = 10.0(u[2]-u[1])
 du[2] = u[1]*(28.0-u[3]) - u[2]
 du[3] = u[1]*u[2] - (8/3)*u[3]
end

function σ_lorenz(du,u,p,t)
 du[1] = 3.0
 du[2] = 3.0
 du[3] = 3.0
end

prob_sde_lorenz = SDEProblem(lorenz,σ_lorenz,[1.0,0.0,0.0],(0.0,10.0))
sol = solve(prob_sde_lorenz)
plot(sol,vars=(1,2,3))
```

問題はデフォルトで対角ノイズになります。非対角ノイズは、`noise_prototype`を設定することで追加できます。

```julia
f = (du,u,p,t) -> du.=1.01u
g = function (du,u,p,t)
  du[1,1] = 0.3u[1]
  du[1,2] = 0.6u[1]
  du[1,3] = 0.9u[1]
  du[1,4] = 0.12u[2]
  du[2,1] = 1.2u[1]
  du[2,2] = 0.2u[2]
  du[2,3] = 0.3u[2]
  du[2,4] = 1.8u[2]
end
prob = SDEProblem(f,g,ones(2),(0.0,1.0),noise_rate_prototype=zeros(2,4))
```

カラー付きノイズは、[`AbstractNoiseProcess`](https://diffeq.sciml.ai/stable/features/noise_process/)を使用して設定できます。たとえば、基礎となるノイズプロセスを`GeometricBrownianMotionProcess`に設定することができます。

```julia
μ = 1.0
σ = 2.0
W = GeometricBrownianMotionProcess(μ,σ,0.0,1.0,1.0)
# ...
# SDEProblemのためにf,g,u0,tspanを定義
# ...
prob = SDEProblem(f,g,u0,tspan,noise=W)
```

StochasticDiffEq.jlは、ランダム常微分方程式を解くことも扱います。これは、[RODEチュートリアル](https://diffeq.sciml.ai/stable/tutorials/rode_example/)で示されています。

```julia
using StochasticDiffEq
function f(u,p,t,W)
  2u*sin(W)
end
u0 = 1.00
tspan = (0.0,5.0)
prob = RODEProblem(f,u0,tspan)
sol = solve(prob,RandomEM(),dt=1/100)
```

## 利用可能なソルバー

利用可能なソルバーのリストについては、[DifferentialEquations.jl SDEソルバーページ](https://diffeq.sciml.ai/stable/solvers/sde_solve/)および[RODEソルバーページ](https://diffeq.sciml.ai/stable/solvers/rode_solve/)を参照してください。
