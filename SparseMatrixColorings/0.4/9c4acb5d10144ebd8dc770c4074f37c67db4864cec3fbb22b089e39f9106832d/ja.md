```
SparseMatrixColorings
```

# SparseMatrixColorings.jl

[![Build Status](https://github.com/gdalle/SparseMatrixColorings.jl/actions/workflows/Test.yml/badge.svg?branch=main)](https://github.com/gdalle/SparseMatrixColorings.jl/actions/workflows/Test.yml?query=branch%3Amain) [![Stable Documentation](https://img.shields.io/badge/docs-stable-blue.svg)](https://gdalle.github.io/SparseMatrixColorings.jl/stable/) [![Dev Documentation](https://img.shields.io/badge/docs-dev-blue.svg)](https://gdalle.github.io/SparseMatrixColorings.jl/dev/) [![Coverage](https://codecov.io/gh/gdalle/SparseMatrixColorings.jl/branch/main/graph/badge.svg)](https://app.codecov.io/gh/gdalle/SparseMatrixColorings.jl) [![Code Style: Blue](https://img.shields.io/badge/code%20style-blue-4495d1.svg)](https://github.com/JuliaDiff/BlueStyle) [![DOI](https://zenodo.org/badge/801999408.svg)](https://zenodo.org/doi/10.5281/zenodo.11314275)

スパースヤコビ行列およびヘッセ行列のための彩色アルゴリズム。

## 始めに

このパッケージをインストールするには、Julia Pkg REPLで以下を実行します：

```julia
pkg> add SparseMatrixColorings
```

## 背景

このパッケージに実装されているアルゴリズムは、以下の文献から取られています：

  * [*What Color Is Your Jacobian? Graph Coloring for Computing Derivatives*](https://epubs.siam.org/doi/10.1137/S0036144504444711), Gebremedhin et al. (2005)
  * [*New Acyclic and Star Coloring Algorithms with Application to Computing Hessians*](https://epubs.siam.org/doi/abs/10.1137/050639879), Gebremedhin et al. (2007)
  * [*Efficient Computation of Sparse Hessians Using Coloring and Automatic Differentiation*](https://pubsonline.informs.org/doi/abs/10.1287/ijoc.1080.0286), Gebremedhin et al. (2009)
  * [*ColPack: Software for graph coloring and related problems in scientific computing*](https://dl.acm.org/doi/10.1145/2513109.2513110), Gebremedhin et al. (2013)

文献の一部（定義など）は、したがって文書にそのままコピーされています。

## 代替案

  * [ColPack.jl](https://github.com/michel2323/ColPack.jl): C++ライブラリ[ColPack](https://github.com/CSCsw/ColPack)へのJuliaインターフェース
  * [SparseDiffTools.jl](https://github.com/JuliaDiff/SparseDiffTools.jl): 一部の彩色アルゴリズムのJulia実装を含む

## 引用

このソフトウェアを引用するには、提供された`CITATION.cff`ファイルを使用してください。リンク[https://zenodo.org/doi/10.5281/zenodo.11314275](https://zenodo.org/doi/10.5281/zenodo.11314275)はZenodoの最新バージョンに解決されます。

## エクスポート

  * [`AbstractColoringResult`](@ref)
  * [`ColoringProblem`](@ref)
  * [`ConstantColoringAlgorithm`](@ref)
  * [`DynamicDegreeBasedOrder`](@ref)
  * [`DynamicLargestFirst`](@ref)
  * [`GreedyColoringAlgorithm`](@ref)
  * [`IncidenceDegree`](@ref)
  * [`LargestFirst`](@ref)
  * [`NaturalOrder`](@ref)
  * [`PerfectEliminationOrder`](@ref)
  * [`RandomOrder`](@ref)
  * [`SmallestLast`](@ref)
  * [`coloring`](@ref)
  * [`column_colors`](@ref)
  * [`column_groups`](@ref)
  * [`compress`](@ref)
  * [`decompress`](@ref)
  * [`decompress!`](@ref)
  * [`decompress_single_color!`](@ref)
  * [`fast_coloring`](@ref)
  * [`ncolors`](@ref)
  * [`row_colors`](@ref)
  * [`row_groups`](@ref)
  * [`sparsity_pattern`](@ref)
