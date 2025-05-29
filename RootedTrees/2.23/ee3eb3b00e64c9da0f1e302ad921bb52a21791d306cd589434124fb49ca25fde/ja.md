# RootedTrees

[![Docs-stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://SciML.github.io/RootedTrees.jl/stable) [![Docs-dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://SciML.github.io/RootedTrees.jl/dev) [![Build Status](https://github.com/SciML/RootedTrees.jl/workflows/CI/badge.svg)](https://github.com/SciML/RootedTrees.jl/actions?query=workflow%3ACI) [![Coverage Status](https://coveralls.io/repos/github/SciML/RootedTrees.jl/badge.svg?branch=main)](https://coveralls.io/github/SciML/RootedTrees.jl?branch=main) [![codecov](https://codecov.io/gh/SciML/RootedTrees.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/SciML/RootedTrees.jl) [![License: MIT](https://img.shields.io/badge/License-MIT-success.svg)](https://opensource.org/licenses/MIT) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.5534590.svg)](https://doi.org/10.5281/zenodo.5534590) <!– [![Downloads](https://shields.io/endpoint?url=https://pkgs.genieframework.com/api/v1/badge/RootedTrees)](https://pkgs.genieframework.com?packages=RootedTrees) –>

根付き木に関する機能のコレクションで、[Julia](https://julialang.org/)におけるルンゲ・クッタ法の順序条件を生成します。このパッケージは、[BSeries.jl](https://github.com/ranocha/BSeries.jl)の基本的な機能も提供します。

## API ドキュメント

RootedTrees.jlのAPIは以下に文書化されています。各関数に関する追加情報は、ドキュメント文字列および[オンラインドキュメント](https://SciML.github.io/RootedTrees.jl/stable)で入手できます。

### 構築

`RootedTree`はレベルシーケンスを使用して表現されます。すなわち、根からのノードの距離を含む`AbstractVector`です。詳細は以下を参照してください。

  * Beyer, Terry, and Sandra Mitchell Hedetniemi. "Constant time generation of rooted trees". SIAM Journal on Computing 9.4 (1980): 706-712. [DOI: 10.1137/0209055](https://doi.org/10.1137/0209055)

`RootedTree`は、次のようにレベルシーケンスから構築できます。

```julia
julia> t = rootedtree([1, 2, 3, 2])
RootedTree{Int64}: [1, 2, 3, 2]
```

[Butcher (Numerical Methods for ODEs, 2016)](https://doi.org/10.1002/9781119121534)の表記法では、この木は`[[τ] τ]`または`(τ ∘ τ) ∘ (τ ∘ τ)`と書くことができ、ここで`∘`は`RootedTree`の非結合的なブッチャー積です。

ブッチャーによって導入された`RootedTree`の表現を取得するには、`butcher_representation`を使用します。

```julia
julia> t = rootedtree([1, 2, 3, 4, 3, 3, 2, 2, 2, 2, 2])
RootedTree{Int64}: [1, 2, 3, 4, 3, 3, 2, 2, 2, 2, 2]

julia> butcher_representation(t)
"[[[τ]τ²]τ⁵]"
```

[Plots.jl](https://github.com/JuliaPlots/Plots.jl)のためのいくつかの簡単なプロットレシピもあります。したがって、`using Plots`を使用しているときに、`plot(t)`を使用して根付き木`t`を視覚化できます。

さらに、`RootedTrees.latexify`というエクスポートされていない関数があり、根付き木`t`のためのLaTeXコードを生成できます。この関数は、LaTeXパッケージ[forest](https://ctan.org/pkg/forest)に基づいています。前文に含める必要がある関連コードは、`RootedTrees.latexify`のドキュメント文字列から取得できます（Julia REPLで`?`と`RootedTrees.latexify`を入力）。同じ形式は、`using Latexify`およびその関数`latexify`を使用する際にも使用されます。詳細は[Latexify.jl](https://github.com/korsbo/Latexify.jl)を参照してください。

### `RootedTree`の反復

`RootedTreeIterator(order::Integer)`を使用して、指定された`order`のすべての`RootedTree`を効率的に反復処理できます。

効率の理由からイテレータは状態を持つため、適切に`copy`を使用する必要があります。例えば、

```julia
julia> map(identity, RootedTreeIterator(4))
4-element Array{RootedTrees.RootedTree{Int64,Array{Int64,1}},1}:
 RootedTree{Int64}: [1, 2, 2, 2]
 RootedTree{Int64}: [1, 2, 2, 2]
 RootedTree{Int64}: [1, 2, 2, 2]
 RootedTree{Int64}: [1, 2, 2, 2]

julia> map(copy, RootedTreeIterator(4))
4-element Array{RootedTrees.RootedTree{Int64,Array{Int64,1}},1}:
 RootedTree{Int64}: [1, 2, 3, 4]
 RootedTree{Int64}: [1, 2, 3, 3]
 RootedTree{Int64}: [1, 2, 3, 2]
 RootedTree{Int64}: [1, 2, 2, 2]
```

### 木に関する関数

`RootedTree`に関する通常の関数が実装されています。詳細は[Butcher (Numerical Methods for ODEs, 2016)](https://doi.org/10.1002/9781119121534)を参照してください。

  * `order(t::RootedTree)`: `RootedTree`の順序、すなわちそのレベルシーケンスの長さ。
  * `σ(t::RootedTree)`または`symmetry(t)`: 根付き木の対称性`σ`、すなわち`t`の特定のラベリング（頂点の）に対する自己同型群の順序。
  * `γ(t::RootedTree)`または`density(t)`: 根付き木の密度`γ(t)`、すなわち`t`のすべての頂点に対するその頂点に根付く部分木の順序の積。
  * `α(t::RootedTree)`: 対称群の下で同等でない`t`の単調ラベリングの数。
  * `β(t::RootedTree)`: 対称群の下で同等でない`t`のラベリングの総数。

さらに、ルンゲ・クッタ法に関連する木に関する関数が実装されています。

  * `elementary_weight(t, A, b, c)`: ルンゲ・クッタ法のブッチャー係数`A, b, c`に対する`RootedTree`の基本的な重みΦ(`t`)を計算します。
  * `derivative_weight(t, A, b, c)`: ルンゲ・クッタ法のブッチャー係数`A, b, c`に対する`t`の導関数重み(ΦᵢD)(`t`)を計算します。
  * `residual_order_condition(t, A, b, c)`: ルンゲ・クッタ法のブッチャー係数`A, b, c`に対する根付き木`t`の基本的な重み`Φ(t)`、密度`γ(t)`、および対称性`σ(t)`を用いた順序条件の残差`(Φ(t) - 1/γ(t)) / σ(t)`。

## 簡易変更履歴

  * v2.16: 根付き木のLaTeX印刷が変更され、色付き根付き木を表現できるようになりました。`RootedTrees.latexify`のドキュメント文字列に記載されているように、LaTeXの前文を更新してください。
  * v2.0: 根付き木は、そのレベルシーケンスの各係数を同じ数だけシフトすることによって導入された同型に基づいて考慮されます。

## 参考文献

[RootedTrees.jl](https://github.com/SciML/RootedTrees.jl)を研究に使用する場合は、次の論文を引用してください。

```bibtex
@article{ketcheson2023computing,
  title={Computing with {B}-series},
  author={Ketcheson, David I and Ranocha, Hendrik},
  journal={ACM Transactions on Mathematical Software},
  volume={49},
  number={2},
  year={2023},
  month={06},
  doi={10.1145/3573384},
  eprint={2111.11680},
  eprinttype={arXiv},
  eprintclass={math.NA}
}
```

さらに、RootedTrees.jlを直接参照することもできます。

```bibtex
@misc{ranocha2019rootedtrees,
  title={{RootedTrees.jl}: {A} collection of functionality around rooted trees
         to generate order conditions for {R}unge-{K}utta methods in {J}ulia
         for differential equations and scientific machine learning ({SciM}L)},
  author={Ranocha, Hendrik and contributors},
  year={2019},
  month={05},
  howpublished={\url{https://github.com/SciML/RootedTrees.jl}},
  doi={10.5281/zenodo.5534590}
}
```
