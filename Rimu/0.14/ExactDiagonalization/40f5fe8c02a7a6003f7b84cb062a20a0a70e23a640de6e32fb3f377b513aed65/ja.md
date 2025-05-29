モジュール `Rimu.ExactDiagonalization` は、[`AbstractHamiltonian`](@ref) 型によって定義された量子多体システムの厳密対角化のためのフレームワークを提供します。

主な使用法は、[`ExactDiagonalizationProblem`](@ref) を定義し、[`solve`](@ref solve(::ExactDiagonalizationProblem)) 関数を使って解決することです。このモジュールは、外部パッケージによって提供されるソルバーを利用するさまざまなソルバーアルゴリズムにアクセスするための統一インターフェースを提供します。

## エクスポート

  * [`ExactDiagonalizationProblem`](@ref)
  * [`BasisSetRepresentation`](@ref)
  * [`build_basis`](@ref)
  * [`KrylovKitSolver`](@ref)
  * [`LinearAlgebraSolver`](@ref)
  * [`ArpackSolver`](@ref)
  * [`LOBPCGSolver`](@ref)
