# Symbolics.jl

[![Github Action CI](https://github.com/JuliaSymbolics/Symbolics.jl/workflows/CI/badge.svg)](https://github.com/JuliaSymbolics/Symbolics.jl/actions) [![codecov](https://codecov.io/gh/JuliaSymbolics/Symbolics.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/JuliaSymbolics/Symbolics.jl) [![Build Status](https://github.com/JuliaSymbolics/Symbolics.jl/workflows/CI/badge.svg)](https://github.com/JuliaSymbolics/Symbolics.jl/actions?query=workflow%3ACI) [![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://docs.sciml.ai/Symbolics/stable/) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://docs.sciml.ai/Symbolics/dev/)

Symbolics.jlは、高速で現代的なプログラミング言語（Julia）のための高速で現代的なコンピュータ代数システム（CAS）です。目標は、ユーザーと同じ言語で直接拡張可能な高性能で並列化されたシンボリック代数システムを持つことです。

## インストール

Symbolics.jlをインストールするには、Juliaパッケージマネージャを使用します：

```julia
julia> using Pkg
julia> Pkg.add("Symbolics")
```

## ドキュメント

パッケージの使用に関する情報は、[安定版ドキュメント](https://juliasymbolics.github.io/Symbolics.jl/stable/)を参照してください。未リリースの機能を含むドキュメントのバージョンについては、[開発中のドキュメント](https://juliasymbolics.github.io/Symbolics.jl/dev/)を使用してください。

## 他のパッケージとの関係

  * [SymbolicUtils.jl](https://github.com/JuliaSymbolics/SymbolicUtils.jl): これはSymbolics.jlのコアであるルール書き換えシステムです。Symbolics.jlはSymbolicUtils.jlを基にして、微分、シンボリック方程式系の解法などをサポートする完全なシンボリック代数システムに拡張します。特定の代数のために新しいCASを構築するための基本が必要な場合、SymbolicUtils.jlがその基盤です。そうでなければ、Symbolics.jlがあなたのためのものです。
  * [ModelingToolkit.jl](https://github.com/SciML/ModelingToolkit.jl): これはSciMLエコシステムのためのシンボリック-数値モデリングシステムです。シンボリック方程式の表現のためにSymbolics.jlを多く使用し、微分などのツールと共に、ODE、SDEなどの一般的なモデリングシステムの表現を追加します。

## 例

```julia
julia> using Symbolics

julia> @variables t x y
julia> D = Differential(t)

julia> z = t + t^2
julia> D(z) # symbolic representation of derivative(t + t^2, t)
Differential(t)(t + t^2)

julia> expand_derivatives(D(z))
1 + 2t

julia> Symbolics.jacobian([x + x*y, x^2 + y],[x, y])
2×2 Matrix{Num}:
 1 + y  x
    2x  1

julia> B = simplify.([t^2 + t + t^2  2t + 4t
                  x + y + y + 2t  x^2 - x^2 + y^2])
2×2 Matrix{Num}:
  t + 2(t^2)   6t
 x + 2t + 2y  y^2

julia> simplify.(substitute.(B, (Dict(x => y^2),)))
2×2 Matrix{Num}:
    t + 2(t^2)   6t
 2t + y^2 + 2y  y^2

julia> substitute.(B, (Dict(x => 2.0, y => 3.0, t => 4.0),))
2×2 Matrix{Num}:
 36.0  24.0
 16.0   9.0
```

## 引用

Symbolics.jlを使用する場合は、[この論文を引用してください](https://dl.acm.org/doi/10.1145/3511528.3511535)（または無料の[arxiv版](https://arxiv.org/abs/2105.03949)を参照してください）。

```bib
@article{10.1145/3511528.3511535,
author = {Gowda, Shashi and Ma, Yingbo and Cheli, Alessandro and Gw\'{o}\'{z}zd\'{z}, Maja and Shah, Viral B. and Edelman, Alan and Rackauckas, Christopher},
title = {High-Performance Symbolic-Numerics via Multiple Dispatch},
year = {2022},
issue_date = {September 2021},
publisher = {Association for Computing Machinery},
address = {New York, NY, USA},
volume = {55},
number = {3},
issn = {1932-2240},
url = {https://doi.org/10.1145/3511528.3511535},
doi = {10.1145/3511528.3511535},
abstract = {As mathematical computing becomes more democratized in high-level languages, high-performance symbolic-numeric systems are necessary for domain scientists and engineers to get the best performance out of their machine without deep knowledge of code optimization. Naturally, users need different term types either to have different algebraic properties for them, or to use efficient data structures. To this end, we developed Symbolics.jl, an extendable symbolic system which uses dynamic multiple dispatch to change behavior depending on the domain needs. In this work we detail an underlying abstract term interface which allows for speed without sacrificing generality. We show that by formalizing a generic API on actions independent of implementation, we can retroactively add optimized data structures to our system without changing the pre-existing term rewriters. We showcase how this can be used to optimize term construction and give a 113x acceleration on general symbolic transformations. Further, we show that such a generic API allows for complementary term-rewriting implementations. Exploiting this feature, we demonstrate the ability to swap between classical term-rewriting simplifiers and e-graph-based term-rewriting simplifiers. We illustrate how this symbolic system improves numerical computing tasks by showcasing an e-graph ruleset which minimizes the number of CPU cycles during expression evaluation, and demonstrate how it simplifies a real-world reaction-network simulation to halve the runtime. Additionally, we show a reaction-diffusion partial differential equation solver which is able to be automatically converted into symbolic expressions via multiple dispatch tracing, which is subsequently accelerated and parallelized to give a 157x simulation speedup. Together, this presents Symbolics.jl as a next-generation symbolic-numeric computing environment geared towards modeling and simulation.},
journal = {ACM Commun. Comput. Algebra},
month = {jan},
pages = {92–96},
numpages = {5}
}
```
