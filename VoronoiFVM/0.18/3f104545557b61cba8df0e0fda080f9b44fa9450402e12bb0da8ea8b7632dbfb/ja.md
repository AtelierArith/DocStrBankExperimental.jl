# VoronoiFVM.jl

[![Build status](https://github.com/j-fu/VoronoiFVM.jl/workflows/linux-macos-windows/badge.svg)](https://github.com/j-fu/VoronoiFVM.jl/actions) [![](https://img.shields.io/badge/docs-stable-blue.svg)](https://j-fu.github.io/VoronoiFVM.jl/stable) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://j-fu.github.io/VoronoiFVM.jl/dev) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3529808.svg)](https://doi.org/10.5281/zenodo.3529808)

Voronoi有限体積法に基づく結合非線形偏微分方程式（楕円-放物線保存則）のソルバーです。ユーザ関数とそのヤコビ行列を評価し、パラメータに対する解の導関数を計算するために、[ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl)および[DiffResults.jl](https://github.com/JuliaDiff/DiffResults.jl)を介した自動微分を使用します。

## 付随パッケージ

  * [VoronoiFVMDiffEq.jl](https://github.com/j-fu/VoronoiFVMDiffEq.jl): VoronoiFVMをDifferentialEquations.jlで使用するためのグルーパッケージ
  * [ExtendableSparse.jl](https://github.com/j-fu/ExtendableSparse.jl): 便利で効率的なスパース行列のアセンブリ
  * [ExtendableGrids.jl](https://github.com/j-fu/ExtendableGrids.jl): 非構造化グリッド管理ライブラリ
  * [SimplexGridFactory.jl](https://github.com/j-fu/SimplexGridFactory.jl): 統一された高レベルメッシュジェネレーターインターフェース
  * [Triangulate.jl](https://github.com/JuliaGeometry/Triangulate.jl): J. Shewchukによる[Triangle](https://www.cs.cmu.edu/~quake/triangle.html)三角形メッシュジェネレーターのJuliaラッパー
  * [TetGen.jl](https://github.com/JuliaGeometry/TetGen.jl): H. Siによる[TetGen](http://www.tetgen.org)四面体メッシュジェネレーターのJuliaラッパー
  * [GridVisualize.jl](https://github.com/j-fu/GridVisualize.jl): ExtendableGrids.jlに関連するグリッドおよび関数の視覚化
  * [PlutoVista.jl](https://github.com/j-fu/PlutoVista.jl): Plutoノートブックで使用するための[GridVisualize.jl](https://github.com/j-fu/GridVisualize.jl)のバックエンド。

## 一部の代替案

  * [GradientRobustMultiPhysics.jl](https://github.com/chmerdon/GradientRobustMultiPhysics.jl): Ch. Merdonによる同じパッケージベースからの勾配ロバストFEMを実装した有限要素ライブラリ
  * [Trixi.jl](https://github.com/trixi-framework/Trixi.jl): ハイパーボリック保存則のための数値シミュレーションフレームワーク
  * [GridAP.jl](https://github.com/gridap/Gridap.jl) Juliaにおける偏微分方程式のグリッドベースの近似
  * [Ferrite.jl](https://github.com/Ferrite-FEM/Ferrite.jl) Juliaの有限要素ツールボックス
  * [FinEtools.jl](https://github.com/PetrKryslUCSD/FinEtools.jl) Juliaの有限要素ツール

## [変更点](https://j-fu.github.io/VoronoiFVM.jl/stable/changes)

このパッケージをあなたの作業で使用する場合は、[CITATION.bib](https://raw.githubusercontent.com/j-fu/VoronoiFVM.jl/master/CITATION.bib)に従って引用してください。

  * [`ContinuousQuantity`](@ref)
  * [`DiscontinuousQuantity`](@ref)
  * [`InterfaceQuantity`](@ref)
  * [`NewtonControl`](@ref)
  * [`NewtonSolverHistory`](@ref)
  * [`SolverControl`](@ref)
  * [`TestFunctionFactory`](@ref)
  * [`TransientSolution`](@ref)
  * [`TransientSolverHistory`](@ref)
  * [`bfacevelocities`](@ref)
  * [`boundary_dirichlet!`](@ref)
  * [`boundary_neumann!`](@ref)
  * [`boundary_robin!`](@ref)
  * [`cartesian!`](@ref)
  * [`check_allocs!`](@ref)
  * [`circular_symmetric!`](@ref)
  * [`coordinates`](@ref)
  * [`data`](@ref)
  * [`details`](@ref)
  * [`dof`](@ref)
  * [`edgelength`](@ref)
  * [`edgevelocities`](@ref)
  * [`embed!`](@ref)
  * [`embedparam`](@ref)
  * [`enable_boundary_species!`](@ref)
  * [`enable_discontinuous_species!`](@ref)
  * [`enable_species!`](@ref)
  * [`eval_jacobian!`](@ref)
  * [`eval_rhs!`](@ref)
  * [`evaluate_residual_and_jacobian`](@ref)
  * [`evolve!`](@ref)
  * [`fbernoulli`](@ref)
  * [`fbernoulli_pm`](@ref)
  * [`fixed_timesteps!`](@ref)
  * [`freqdomain_impedance`](@ref)
  * [`getdof`](@ref)
  * [`history`](@ref)
  * [`history_details`](@ref)
  * [`history_summary`](@ref)
  * [`impedance`](@ref)
  * [`integrate`](@ref)
  * [`mass_matrix`](@ref)
  * [`meas`](@ref)
  * [`measurement_derivative`](@ref)
  * [`nodeflux`](@ref)
  * [`num_dof`](@ref)
  * [`parameters`](@ref)
  * [`physics!`](@ref)
  * [`prepare_diffeq!`](@ref)
  * [`project`](@ref)
  * [`ramp`](@ref)
  * [`region`](@ref)
  * [`setdof!`](@ref)
  * [`solve`](@ref)
  * [`solve!`](@ref)
  * [`spherical_symmetric!`](@ref)
  * [`subgrids`](@ref)
  * [`testfunction`](@ref)
  * [`time`](@ref)
  * [`transient_solution`](@ref)
  * [`unknown_indices`](@ref)
  * [`unknowns`](@ref)
  * [`update_grid!`](@ref)
  * [`value`](@ref)
  * [`viewK`](@ref)
  * [`viewL`](@ref)
  * [`views`](@ref)
