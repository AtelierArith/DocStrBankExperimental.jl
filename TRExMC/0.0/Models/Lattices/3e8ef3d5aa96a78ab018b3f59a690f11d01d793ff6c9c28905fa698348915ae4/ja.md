module Lattices

任意のシミュレーションモデルが基盤となる幾何学的構造にアクセスするためのメインエントリポイント。現在、以下のサブファイルで構成されています：

  * [`AbstractLattices.jl`]:

      * すべての格子のスーパタイプとして[`AbstractLattice](@ref)を定義するインターフェースモジュール
  * [`CubicLattices.jl`]: 

      * [`AbstractCubicLattice`](@ref)サブタイプを定義
      * [`CubicLattice2D`](@ref) `<: AbstractCubicLattice`および[`CubicLattice2DParams`](@ref)を実装
