# DiffEqBayes.jl

[![Join the chat at https://julialang.zulipchat.com #sciml-bridged](https://img.shields.io/static/v1?label=Zulip&message=chat&color=9558b2&labelColor=389826)](https://julialang.zulipchat.com/#narrow/stream/279055-sciml-bridged) [![Global Docs](https://img.shields.io/badge/docs-SciML-blue.svg)](https://docs.sciml.ai/DiffEqBayes/stable/)

[![codecov](https://codecov.io/gh/SciML/DiffEqBayes.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/SciML/DiffEqBayes.jl) [![Build Status](https://github.com/SciML/DiffEqBayes.jl/workflows/CI/badge.svg)](https://github.com/SciML/DiffEqBayes.jl/actions?query=workflow%3ACI)

[![ColPrac: Contributor's Guide on Collaborative Practices for Community Packages](https://img.shields.io/badge/ColPrac-Contributor%27s%20Guide-blueviolet)](https://github.com/SciML/ColPrac) [![SciML Code Style](https://img.shields.io/static/v1?label=code%20style&message=SciML&color=9558b2&labelColor=389826)](https://github.com/SciML/SciMLStyle)

このリポジトリは、ベイズ法を使用して微分方程式のパラメータを推定するための拡張機能のセットです。これは、[CmdStan.jl](https://stanjulia.github.io/CmdStan.jl/stable/)、[Turing.jl](https://turing.ml/stable/docs/using-turing/)、[DynamicHMC.jl](https://www.tamaspapp.eu/DynamicHMC.jl/stable/)および[ApproxBayes.jl](https://github.com/marcjwilliams1/ApproxBayes.jl)を使用して、[DifferentialEquations.jl](https://docs.sciml.ai/DiffEqDocs/stable/)インターフェースを介して指定された微分方程式問題のベイズ推定を実行することを可能にします。

始めるには、まず次のコマンドを使用してこのリポジトリを追加する必要があります。

```julia
Pkg.add("DiffEqBayes")
using DiffEqBayes
```

## チュートリアルとドキュメント

パッケージの使用に関する情報は、[安定版のドキュメントを参照してください](https://docs.sciml.ai/DiffEqBayes/stable/)。未リリースの機能を含むドキュメントのバージョンについては、[開発中のドキュメントを使用してください](https://docs.sciml.ai/DiffEqBayes/dev/)。

## 例

```julia
using ParameterizedFunctions, OrdinaryDiffEq, RecursiveArrayTools, Distributions
f1 = @ode_def LotkaVolterra begin
    dx = a * x - x * y
    dy = -3 * y + x * y
end a

p = [1.5]
u0 = [1.0, 1.0]
tspan = (0.0, 10.0)
prob1 = ODEProblem(f1, u0, tspan, p)

σ = 0.01                         # ノイズ、今のところ固定
t = collect(1.0:10.0)   # 観測時間
sol = solve(prob1, Tsit5())
priors = [Normal(1.5, 1)]
randomized = VectorOfArray([(sol(t[i]) + σ * randn(2)) for i in 1:length(t)])
data = convert(Array, randomized)

using CmdStan #Stanバックエンドを使用するために必要
bayesian_result_stan = stan_inference(prob1, t, data, priors)

bayesian_result_turing = turing_inference(prob1, Tsit5(), t, data, priors)

using DynamicHMC #DynamicHMCバックエンドに必要
bayesian_result_hmc = dynamichmc_inference(prob1, Tsit5(), t, data, priors)

bayesian_result_abc = abc_inference(prob1, Tsit5(), t, data, priors)
```

### save_idxsを使用して観測可能変数を宣言する

モデルのすべての変数に対してデータが常にあるわけではありません。特定の潜在変数の場合、`save_idxs`キーワード引数を利用して観測された変数を宣言し、以下に示すように任意のバックエンドを使用して推論を実行できます。

```julia
sol = solve(prob1, Tsit5(), save_idxs = [1])
randomized = VectorOfArray([(sol(t[i]) + σ * randn(1)) for i in 1:length(t)])
data = convert(Array, randomized)

using CmdStan #Stanバックエンドを使用するために必要
bayesian_result_stan = stan_inference(prob1, t, data, priors, save_idxs = [1])

bayesian_result_turing = turing_inference(prob1, Tsit5(), t, data, priors, save_idxs = [1])

using DynamicHMC #DynamicHMCバックエンドに必要
bayesian_result_hmc = dynamichmc_inference(prob1, Tsit5(), t, data, priors, save_idxs = [1])

bayesian_result_abc = abc_inference(prob1, Tsit5(), t, data, priors, save_idxs = [1])
```
