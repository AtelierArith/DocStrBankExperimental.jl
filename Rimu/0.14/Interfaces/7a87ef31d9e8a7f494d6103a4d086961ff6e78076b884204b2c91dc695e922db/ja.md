```
module Interfaces
```

このモジュールには、`Rimu`のアルゴリズムや動作を拡張および修正するために使用できるインターフェースが含まれています。

# インターフェース

インターフェースの定義については、リンクを参照してください！

  * [`AbstractHamiltonian`](@ref) は [`Hamiltonians`](@ref Main.Hamiltonians) を定義するためのものです
  * [`AbstractOperator`](@ref) は観測可能な演算子を定義するためのものです
  * [`AbstractDVec`](@ref) は [`DictVectors`](@ref Main.DictVectors) のように `Rimu` のデータ構造を定義するためのものです
  * [`StochasticStyle`](@ref) は [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem) によって使用される確率的アルゴリズムを制御するためのものです。これは [`StochasticStyles`](@ref Main.StochasticStyles) に実装されています。

# 追加のエクスポート

## [`AbstractHamiltonian`](@ref) のためのインターフェース関数：

  * [`diagonal_element`](@ref)
  * [`num_offdiagonals`](@ref)
  * [`get_offdiagonal`](@ref)
  * [`offdiagonals`](@ref).
  * [`random_offdiagonal`](@ref)
  * [`starting_address`](@ref)
  * [`LOStructure`](@ref)
  * [`allows_address_type`](@ref)

## [`AbstractDVec`](@ref) と [`StochasticStyle`](@ref) を使った作業

  * [`deposit!`](@ref)
  * [`default_style`](@ref)
  * [`CompressionStrategy`](@ref)
  * [VectorInterface.jl](https://github.com/Jutho/VectorInterface.jl) からのインターフェース。

## Rimu.jl が FCIQMC を行うために使用する関数：

  * [`apply_column!`](@ref)
  * [`apply_operator!`](@ref)
  * [`step_stats`](@ref)
