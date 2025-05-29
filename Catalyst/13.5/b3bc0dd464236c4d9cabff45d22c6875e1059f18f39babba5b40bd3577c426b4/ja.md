# Catalyst.jl

[![Join the chat at https://julialang.zulipchat.com #sciml-bridged](https://img.shields.io/static/v1?label=Zulip&message=chat&color=9558b2&labelColor=389826)](https://julialang.zulipchat.com/#narrow/stream/279055-sciml-bridged) [![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://docs.sciml.ai/Catalyst/stable/) [![API Stable](https://img.shields.io/badge/API-stable-blue.svg)](https://docs.sciml.ai/Catalyst/stable/api/catalyst_api/) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://docs.sciml.ai/Catalyst/dev/) [![API Dev](https://img.shields.io/badge/API-dev-blue.svg)](https://docs.sciml.ai/Catalyst/dev/api/catalyst_api/)

[![Build Status](https://github.com/SciML/Catalyst.jl/workflows/CI/badge.svg)](https://github.com/SciML/Catalyst.jl/actions?query=workflow%3ACI) [![codecov.io](https://codecov.io/gh/SciML/Catalyst.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/SciML/Catalyst.jl) [![Coverage Status](https://coveralls.io/repos/github/SciML/Catalyst.jl/badge.svg?branch=master)](https://coveralls.io/github/SciML/Catalyst.jl?branch=master)

[![ColPrac: Contributor's Guide on Collaborative Practices for Community Packages](https://img.shields.io/badge/ColPrac-Contributor's%20Guide-blueviolet)](https://github.com/SciML/ColPrac) [![SciML Code Style](https://img.shields.io/static/v1?label=code%20style&message=SciML&color=9558b2&labelColor=389826)](https://github.com/SciML/SciMLStyle)

Catalyst.jlは、化学反応ネットワークの分析と高性能シミュレーションのためのシンボリックモデリングパッケージです。Catalystは、プログラム的に作成することも、Catalystのドメイン固有言語（DSL）を使用して簡単に指定することができるシンボリック[`ReactionSystem`](https://docs.sciml.ai/Catalyst/stable/catalyst_functionality/programmatic_CRN_construction/)を定義します。[ModelingToolkit](https://github.com/SciML/ModelingToolkit.jl)と[Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl)を活用することで、Catalystは自動ベクトル化と並列処理を通じて大規模なシミュレーションを可能にします。シンボリック`ReactionSystem`は、ModelingToolkitベースのモデルを生成するために使用でき、質量作用ODEモデル、化学ランジュバンSDEモデル、確率的化学動力学ジャンププロセスモデルなどのシミュレーションやパラメータ推定を容易に行うことができます。生成されたモデルは、感度分析、パラメータ推定、機械学習アプリケーションなどのための高レベルのSciMLパッケージを含む、より広範な[SciML](https://sciml.ai)エコシステム全体でソルバーと共に使用できます。

## Breaking changes and new features

**NOTE:** バージョン13は破壊的リリースであり、DSL表記を簡素化しながらも、`ReactionSystem`を直接構築する際の化学種のシンボリック指定方法の変更や、ODEまたは代数制約方程式を含める方法の簡素化が行われています。

破壊的変更と新機能は、[HISTORY.md](HISTORY.md)ファイルに要約されています。

## Tutorials and documentation

パッケージの最新のチュートリアルと情報は、[stable documentation](https://docs.sciml.ai/Catalyst/stable/)で入手できます。[in-development documentation](https://docs.sciml.ai/Catalyst/dev/)は、現在のマスターブランチの未リリース機能について説明しています。

いくつかのYoutubeビデオチュートリアルと概要も利用可能ですが、これらは古いCatalystバージョンを使用しており、やや異なる表記法（たとえば、反応ネットワークの構築において）を使用していることに注意してください：

  * JuliaCon 2022から：Catalystとそのより高度な機能の使用方法を概説する3時間のチュートリアルワークショップ。[Workshop video](https://youtu.be/tVfxT09AtWQ)、[Workshop Pluto.jl Notebooks](https://github.com/SciML/JuliaCon2022_Catalyst_Workshop)。
  * SIAM CSE 2021から：バージョン6のCatalystの短い15分の概要は、[Modeling Biochemical Systems with Catalyst.jl](https://www.youtube.com/watch?v=5p1PJE5A5Jw)というトークで入手可能です。
  * JuliaCon 2018から：古いバージョンでDiffEqBiologicalとして知られていたCatalystの短い13分の概要は、[Efficient Modelling of Biochemical Reaction Networks](https://www.youtube.com/watch?v=s1e72k5XD6s)というトークで入手可能です。

## Features

  * DSLは、化学反応を手動で指定するためのシンプルで読みやすい形式を提供します。
  * Catalyst `ReactionSystem`は、[ModelingToolkit.jl](https://docs.sciml.ai/ModelingToolkit/stable/)と[Symbolics.jl](https://docs.sciml.ai/Symbolics/stable/)に基づいて構築された反応ネットワークのシンボリック表現を提供します。
  * 非整数（例：`Float64`）のストイキオメトリック係数がODEモデルの生成をサポートし、すべてのシステムタイプに対してストイキオメトリック係数のシンボリック表現がサポートされています。
  * [Catalyst.jl API](http://docs.sciml.ai/Catalyst/stable/api/catalyst_api)は、ネットワークの拡張、プログラム的なネットワークの構築、ネットワーク分析、および複数のネットワークを組み合わせるための機能を提供します。
  * DSLによって生成された`ReactionSystem`は、シンボリックODE、SDE、およびジャンププロセス表現を含むさまざまな`ModelingToolkit.AbstractSystem`に変換できます。
  * 結合された微分方程式と代数制約方程式をCatalystモデルに含めることができ、ODEまたは定常状態方程式への変換中に組み込まれます。
  * 保存則を検出して適用することで、システムサイズを削減し、ODE、SDE、および定常状態方程式への変換中に非特異ヤコビアンを生成できます。
  * ModelingToolkitを活用することで、ユーザーはソルバーで使用するための最適化されたシステム表現を生成するためのさまざまなオプションを持っています。これには、密なまたは疎なヤコビアンの構築、生成された導関数関数のマルチスレッドまたは並列化、Gillespieタイプのシミュレーションのための最適化されたジャンプタイプへの反応の自動分類、ジャンプシステムのための依存関係グラフの自動構築などが含まれます。
  * 生成されたシステムは、任意の[DifferentialEquations.jl](https://docs.sciml.ai/DiffEqDocs/stable/) ODE/SDE/ジャンプソルバーを使用して解決でき、`EnsembleProblem`内で並列化されたパラメータスイープや統計的サンプリングを実行するために使用できます。ソリューションを視覚化するためのプロットレシピが利用可能です。
  * [Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl)のシンボリック表現とJuliaの`Expr`は、結果のODE、SDE、またはジャンプモデル内の決定論的および確率的項を決定するすべての速度法則および関数に対して取得できます。
  * [Latexify](https://korsbo.github.io/Latexify.jl/stable/)を使用して、生成された数学モデルまたは基礎となる反応のセットに対応するLaTeX表現を生成できます。
  * [Graphviz](https://graphviz.org/)を使用して、反応ネットワークグラフを生成および視覚化できます。（[Catlab.jl](https://algebraicjulia.github.io/Catlab.jl/stable/)で作成されたGraphvizインターフェースを再利用しています。）

## Packages supporting Catalyst

  * Catalyst [`ReactionSystem`](@ref)は、[SBMLToolkit.jl](https://github.com/SciML/SBMLToolkit.jl)を介してSBMLファイルからインポートでき、[ReactionNetworkImporters.jl](https://github.com/SciML/ReactionNetworkImporters.jl)を使用してBioNetGen .netファイルやさまざまなストイキオメトリック行列ネットワーク表現からインポートできます。
  * [MomentClosure.jl](https://github.com/augustinas1/MomentClosure.jl)は、Catalystで定義された反応ネットワークから化学マスター方程式のモーメント閉包近似を表すシンボリックModelingToolkit `ODESystem`を生成することを可能にします。
  * [FiniteStateProjection.jl](https://github.com/kaandocal/FiniteStateProjection.jl)は、Catalystで定義された反応ネットワークから化学マスター方程式モデルの構築と数値解法を可能にします。
  * [DelaySSAToolkit.jl](https://github.com/palmtree2013/DelaySSAToolkit.jl)は、Catalyst反応ネットワークモデルに遅延を追加し、遅延モデルを持つ確率的化学動力学をシミュレートできます。
  * [BondGraphs.jl](https://github.com/jedforrest/BondGraphs.jl)は、Catalystモデルを入力として受け取るボンドグラフモデルを構築および分析するためのパッケージです。
  * [PEtab.jl](https://github.com/sebapersson/PEtab.jl)は、反応ネットワークODEをデータにフィットさせるためのPEtab形式を実装するパッケージです。入力はSBMLファイルまたはCatalyst `ReactionSystem`として提供できます。

## Illustrative examples

#### Gillespie simulations of Michaelis-Menten enzyme kinetics

```julia
using Catalyst, Plots, JumpProcesses
rs = @reaction_network begin
  c1, S + E --> SE
  c2, SE --> S + E
  c3, SE --> P + E
end
p  = (:c1 => 0.00166, :c2 => 0.0001, :c3 => 0.1)
tspan = (0., 100.)
u0 = [:S => 301, :E => 100, :SE => 0, :P => 0]

# solve JumpProblem
dprob = DiscreteProblem(rs, u0, tspan, p)
jprob = JumpProblem(rs, dprob, Direct())
jsol = solve(jprob, SSAStepper())
plot(jsol; lw = 2, title = "Gillespie: Michaelis-Menten Enzyme Kinetics")
```

![](https://user-images.githubusercontent.com/1814174/87864114-3bf9dd00-c932-11ea-83a0-58f38aee8bfb.png)

#### Adaptive time stepping SDEs for a birth-death process

```julia
using Catalyst, Plots, StochasticDiffEq
rs = @reaction_network begin
  c1, X --> 2X
  c2, X --> 0
  c3, 0 --> X
end
p     = (:c1 => 1.0, :c2 => 2.0, :c3 => 50.)
tspan = (0.,10.)
u0    = [:X => 5.]
sprob = SDEProblem(rs, u0, tspan, p)
ssol  = solve(sprob, LambaEM(), reltol=1e-3)
plot(ssol; lw = 2, title = "Adaptive SDE: Birth-Death Process")
```

![](https://user-images.githubusercontent.com/1814174/87864113-3bf9dd00-c932-11ea-8275-f903eef90b91.png)

## Getting help

Catalystの開発者は、[Julia Discourse](https://discourse.julialang.org/)、[Julia Slack](https://julialang.slack.com)の#sciml-bridgedおよび#sciml-sysbioチャンネル、[Julia Zulip sciml-bridgedチャンネル](https://julialang.zulipchat.com/#narrow/stream/279055-sciml-bridged)で活動しています。バグや機能リクエストについては、[issueを開いてください](https://github.com/SciML/Catalyst.jl/issues)。

## Supporting and citing Catalyst.jl

このエコシステムのソフトウェアは、学術研究の一環として開発されました。これをサポートしたい場合は、リポジトリにスターを付けてください。このようなメトリクスは、将来的に資金を確保するのに役立つかもしれません。研究、教育、またはその他の活動の一環としてCatalystを使用する場合は、私たちの研究を引用していただけると幸いです：

```
@article{CatalystPLOSCompBio2023,
    doi = {10.1371/journal.pcbi.1011530},
    author = {Loman, Torkel E. AND Ma, Yingbo AND Ilin, Vasily AND Gowda, Shashi AND Korsbo, Niklas AND Yewale, Nikhil AND Rackauckas, Chris AND Isaacson, Samuel A.},
    journal = {PLOS Computational Biology},
    publisher = {Public Library of Science},
    title = {Catalyst: Fast and flexible modeling of reaction networks},
    year = {2023},
    month = {10},
    volume = {19},
    url = {https://doi.org/10.1371/journal.pcbi.1011530},
    pages = {1-19},
    number = {10},
}
```
