# ModelingToolkit.jl

[![Join the chat at https://julialang.zulipchat.com #sciml-bridged](https://img.shields.io/static/v1?label=Zulip&message=chat&color=9558b2&labelColor=389826)](https://julialang.zulipchat.com/#narrow/stream/279055-sciml-bridged) [![Global Docs](https://img.shields.io/badge/docs-SciML-blue.svg)](https://docs.sciml.ai/ModelingToolkit/stable/)

[![codecov](https://codecov.io/gh/SciML/ModelingToolkit.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/SciML/ModelingToolkit.jl) [![Coverage Status](https://coveralls.io/repos/github/SciML/ModelingToolkit.jl/badge.svg?branch=master)](https://coveralls.io/github/SciML/ModelingToolkit.jl?branch=master) [![Build Status](https://github.com/SciML/ModelingToolkit.jl/workflows/CI/badge.svg)](https://github.com/SciML/ModelingToolkit.jl/actions?query=workflow%3ACI)

[![ColPrac: Contributor's Guide on Collaborative Practices for Community Packages](https://img.shields.io/badge/ColPrac-Contributor%27s%20Guide-blueviolet)](https://github.com/SciML/ColPrac) [![SciML Code Style](https://img.shields.io/static/v1?label=code%20style&message=SciML&color=9558b2&labelColor=389826)](https://github.com/SciML/SciMLStyle)

ModelingToolkit.jlは、科学計算および科学機械学習における高性能なシンボリック数値計算のためのモデリングフレームワークです。ユーザーはモデルの高レベルな記述を提供し、シンボリック前処理を通じてモデルを分析および強化することができます。ModelingToolkitは、ヤコビ行列やヘッセ行列のようなモデルコンポーネントのための高速関数を自動的に生成し、計算を自動的にスパース化および並列化します。インデックス削減などの自動変換をモデルに適用することで、数値ソルバーが扱いやすくなります。

パッケージの使用に関する情報は、[安定版のドキュメント](https://docs.sciml.ai/ModelingToolkit/stable/)を参照してください。未リリースの機能を含むドキュメントのバージョンについては、[開発中のドキュメント](https://docs.sciml.ai/ModelingToolkit/dev/)を使用してください。

## 標準ライブラリ

ModelingToolkitコンポーネントとブロックの標準ライブラリについては、[ModelingToolkitStandardLibrary](https://docs.sciml.ai/ModelingToolkitStandardLibrary/stable/)をチェックしてください。

## 高レベルの例

まず、ローレンツ方程式の2次のリフを定義し、シンボリックに1次系に低下させ、数値積分器のためのヤコビ行列関数をシンボリックに生成し、解きます。

```julia
using OrdinaryDiffEqDefault, ModelingToolkit
using ModelingToolkit: t_nounits as t, D_nounits as D

@parameters σ ρ β
@variables x(t) y(t) z(t)

eqs = [D(D(x)) ~ σ * (y - x),
    D(y) ~ x * (ρ - z) - y,
    D(z) ~ x * y - β * z]

@mtkbuild sys = ODESystem(eqs, t)

u0 = [D(x) => 2.0,
    x => 1.0,
    y => 0.0,
    z => 0.0]

p = [σ => 28.0,
    ρ => 10.0,
    β => 8 / 3]

tspan = (0.0, 100.0)
prob = ODEProblem(sys, u0, tspan, p, jac = true)
sol = solve(prob)
using Plots
plot(sol, idxs = (x, y))
```

![Lorenz2](https://user-images.githubusercontent.com/1814174/79118645-744eb580-7d5c-11ea-9c37-13c4efd585ca.png)

これにより、高速なヤコビ行列関数が自動的に生成され、関数を直接構築するよりも最適化されます。さらに、ModelingToolkitを使用して複数のODEサブシステムを構成することができます。次に、相互作用する2つのローレンツ方程式を定義し、結果として得られる微分代数方程式（DAE）をシミュレートします。

```julia
using DifferentialEquations, ModelingToolkit
using ModelingToolkit: t_nounits as t, D_nounits as D

@parameters σ ρ β
@variables x(t) y(t) z(t)

eqs = [D(x) ~ σ * (y - x),
    D(y) ~ x * (ρ - z) - y,
    D(z) ~ x * y - β * z]

@named lorenz1 = ODESystem(eqs, t)
@named lorenz2 = ODESystem(eqs, t)

@variables a(t)
@parameters γ
connections = [0 ~ lorenz1.x + lorenz2.y + a * γ]
@mtkbuild connected = ODESystem(connections, t, systems = [lorenz1, lorenz2])

u0 = [lorenz1.x => 1.0,
    lorenz1.y => 0.0,
    lorenz1.z => 0.0,
    lorenz2.x => 0.0,
    lorenz2.y => 1.0,
    lorenz2.z => 0.0,
    a => 2.0]

p = [lorenz1.σ => 10.0,
    lorenz1.ρ => 28.0,
    lorenz1.β => 8 / 3,
    lorenz2.σ => 10.0,
    lorenz2.ρ => 28.0,
    lorenz2.β => 8 / 3,
    γ => 2.0]

tspan = (0.0, 100.0)
prob = ODEProblem(connected, u0, tspan, p)
sol = solve(prob)

using Plots
plot(sol, idxs = (a, lorenz1.x, lorenz2.z))
```

![](https://user-images.githubusercontent.com/17304743/187790221-528046c3-dbdb-4853-b977-799596c147f3.png)

# 引用

ModelingToolkit.jlを研究で使用する場合は、[この論文](https://arxiv.org/abs/2103.05244)を引用してください：

```
@misc{ma2021modelingtoolkit,
      title={ModelingToolkit: A Composable Graph Transformation System For Equation-Based Modeling},
      author={Yingbo Ma and Shashi Gowda and Ranjan Anantharaman and Chris Laughman and Viral Shah and Chris Rackauckas},
      year={2021},
      eprint={2103.05244},
      archivePrefix={arXiv},
      primaryClass={cs.MS}
}
```
