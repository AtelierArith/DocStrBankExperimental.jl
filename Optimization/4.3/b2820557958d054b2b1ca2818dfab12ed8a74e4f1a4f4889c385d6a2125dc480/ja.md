# Optimization.jl

[![Join the chat at https://julialang.zulipchat.com #sciml-bridged](https://img.shields.io/static/v1?label=Zulip&message=chat&color=9558b2&labelColor=389826)](https://julialang.zulipchat.com/#narrow/stream/279055-sciml-bridged) [![Global Docs](https://img.shields.io/badge/docs-SciML-blue.svg)](https://docs.sciml.ai/Optimization/stable/)

[![codecov](https://codecov.io/gh/SciML/Optimization.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/SciML/Optimization.jl) [![Build Status](https://github.com/SciML/Optimization.jl/workflows/CI/badge.svg)](https://github.com/SciML/Optimization.jl/actions?query=workflow%3ACI)

[![ColPrac: Contributor's Guide on Collaborative Practices for Community Packages](https://img.shields.io/badge/ColPrac-Contributor%27s%20Guide-blueviolet)](https://github.com/SciML/ColPrac) [![SciML Code Style](https://img.shields.io/static/v1?label=code%20style&message=SciML&color=9558b2&labelColor=389826)](https://github.com/SciML/SciMLStyle)

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.7738525.svg)](https://doi.org/10.5281/zenodo.7738525)

Optimization.jlは、通常のグローバル最適化パッケージを超えた範囲を持つパッケージです。Optimization.jlは、見つけられるすべての最適化パッケージ（ローカルおよびグローバル）を1つの統一されたJuliaインターフェースにまとめることを目指しています。つまり、1つのパッケージを学べば、すべてを学ぶことができるのです！Optimization.jlは、自動微分との統合など、いくつかの高レベルの機能を追加し、ほとんどのケースでの使用を非常に簡単にし、すべてのオプションを単一の統一インターフェースで提供します。

## インストール

Juliaが正しくインストールされていると仮定すると、標準的な方法でOptimization.jlをインポートするだけで済みます：

```julia
using Pkg
Pkg.add("Optimization")
```

Optimization.jlのコア機能に関連するパッケージは適切にインポートされ、ほとんどの場合、依存関係の手動インストールを心配する必要はありません。以下は、特定の最適化アルゴリズムを使用する予定がある場合に明示的にインストールする必要があるパッケージのリストです：

  * OptimizationBBO for [BlackBoxOptim.jl](https://github.com/robertfeldt/BlackBoxOptim.jl)
  * OptimizationEvolutionary for [Evolutionary.jl](https://github.com/wildart/Evolutionary.jl) (see also [this documentation](https://wildart.github.io/Evolutionary.jl/dev/))
  * OptimizationGCMAES for [GCMAES.jl](https://github.com/AStupidBear/GCMAES.jl)
  * OptimizationMOI for [MathOptInterface.jl](https://github.com/jump-dev/MathOptInterface.jl) (usage of algorithm via MathOptInterface API; see also the API [documentation](https://jump.dev/MathOptInterface.jl/stable/))
  * OptimizationMetaheuristics for [Metaheuristics.jl](https://github.com/jmejia8/Metaheuristics.jl) (see also [this documentation](https://jmejia8.github.io/Metaheuristics.jl/stable/))
  * OptimizationMultistartOptimization for [MultistartOptimization.jl](https://github.com/tpapp/MultistartOptimization.jl) (see also [this documentation](https://juliahub.com/docs/MultistartOptimization/cVZvi/0.1.0/))
  * OptimizationNLopt for [NLopt.jl](https://github.com/JuliaOpt/NLopt.jl) (usage via the NLopt API; see also the available [algorithms](https://nlopt.readthedocs.io/en/latest/NLopt_Algorithms/))
  * OptimizationNOMAD for [NOMAD.jl](https://github.com/bbopt/NOMAD.jl) (see also [this documentation](https://bbopt.github.io/NOMAD.jl/stable/))
  * OptimizationNonconvex for [Nonconvex.jl](https://github.com/JuliaNonconvex/Nonconvex.jl) (see also [this documentation](https://julianonconvex.github.io/Nonconvex.jl/stable/))
  * OptimizationQuadDIRECT for [QuadDIRECT.jl](https://github.com/timholy/QuadDIRECT.jl)
  * OptimizationSpeedMapping for [SpeedMapping.jl](https://github.com/NicolasL-S/SpeedMapping.jl) (see also [this documentation](https://nicolasl-s.github.io/SpeedMapping.jl/stable/))

## チュートリアルとドキュメント

パッケージの使用に関する情報は、[安定版のドキュメント](https://docs.sciml.ai/Optimization/stable/)を参照してください。未公開の機能を含むドキュメントのバージョンについては、[開発中のドキュメント](https://docs.sciml.ai/Optimization/dev/)を使用してください。

## 例

```julia
using Optimization
rosenbrock(x, p) = (p[1] - x[1])^2 + p[2] * (x[2] - x[1]^2)^2
x0 = zeros(2)
p = [1.0, 100.0]

prob = OptimizationProblem(rosenbrock, x0, p)

using OptimizationOptimJL
sol = solve(prob, NelderMead())

using OptimizationBBO
prob = OptimizationProblem(rosenbrock, x0, p, lb = [-1.0, -1.0], ub = [1.0, 1.0])
sol = solve(prob, BBO_adaptive_de_rand_1_bin_radiuslimited())
```

Optim.jlはOptimization.jlのコア依存関係ですが、BlackBoxOptim.jlはそうではなく、すでにインストールされている必要があります（上記のリストを参照）。

*警告:* 2番目の最適化タスク（`BBO_adaptive_de_rand_1_bin_radiuslimited()`）の出力は、現在「Status: failure (reached maximum number of iterations)」と誤解を招くものです。しかし、実際には収束が達成されており、混乱を招くメッセージはOptim.jlの出力構造に依存しているために生じています（最大反復回数に達する状況は正しく失敗と見なされます）。改善された出力構造はすぐに実装される予定です。

最初の最適化タスク（`NelderMead()`アルゴリズムを使用）の出力は以下の通りです：

```
* Status: success

* Candidate solution
   Final objective value:     3.525527e-09

* Found with
   Algorithm:     Nelder-Mead

* Convergence measures
   √(Σ(yᵢ-ȳ)²)/n ≤ 1.0e-08

* Work counters
   Seconds run:   0  (vs limit Inf)
   Iterations:    60
   f(x) calls:    118
```

他の方法も同様に探ることができます：

```julia
using ForwardDiff
f = OptimizationFunction(rosenbrock, Optimization.AutoForwardDiff())
prob = OptimizationProblem(f, x0, p)
sol = solve(prob, BFGS())
```

例えば、上記の最適化タスクは以下の出力を生成します：

```
* Status: success

* Candidate solution
   Final objective value:     7.645684e-21

* Found with
   Algorithm:     BFGS

* Convergence measures
   |x - x'|               = 3.48e-07 ≰ 0.0e+00
   |x - x'|/|x'|          = 3.48e-07 ≰ 0.0e+00
   |f(x) - f(x')|         = 6.91e-14 ≰ 0.0e+00
   |f(x) - f(x')|/|f(x')| = 9.03e+06 ≰ 0.0e+00
   |g(x)|                 = 2.32e-09 ≤ 1.0e-08

* Work counters
   Seconds run:   0  (vs limit Inf)
   Iterations:    16
   f(x) calls:    53
   ∇f(x) calls:   53
```

```julia
prob = OptimizationProblem(f, x0, p, lb = [-1.0, -1.0], ub = [1.0, 1.0])
sol = solve(prob, Fminbox(GradientDescent()))
```

これらの例は、Optimization.jlが最適化タスクを指定する直感的な方法を提供し、幅広い最適化アルゴリズムへの比較的簡単なアクセスを提供することを明確に示しています。
