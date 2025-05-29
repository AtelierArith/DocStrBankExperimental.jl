```julia
mutable struct System{Tv, Tc, Ti, Tm, TSpecMat<:(AbstractMatrix)} <: VoronoiFVM.AbstractSystem{Tv, Tc, Ti, Tm}
```

有限体積システムのデータを保持する構造体。

[`AbstractSystem`](@ref) のサブタイプ。

型パラメータ:

  * TSpecMat: 種情報を格納する行列の型 (Matrix または SparseMatrixCSC)

他の型パラメータについては、[`AbstractSystem`](@ref) を参照してください。

  * `grid::ExtendableGrids.ExtendableGrid`: グリッド
  * `physics::VoronoiFVM.Physics`: 物理データ
  * `boundary_values::Matrix`: 境界条件値の配列
  * `boundary_factors::Matrix`: 境界条件係数の配列
  * `region_species::AbstractMatrix`: 内部領域の種番号を含む行列
  * `bregion_species::AbstractMatrix`: 境界領域の種番号を含む行列
  * `node_dof::AbstractMatrix`: 各ノードの自由度番号を含む行列
  * `matrixtype::Symbol`: - :multidiagonal  (現在無効)

      * :sparse
      * :banded
      * :tridiagonal
  * `species_homogeneous::Bool`: 各ノードの未知数の数が一定であるかどうかを示すフラグ
  * `num_quantities::Any`: システム上で定義された量の数
  * `num_parameters::Any`: システムが依存するパラメータの数。
  * `assembly_data::Union{Nothing, VoronoiFVM.AbstractAssemblyData{Tc, Ti}} where {Tc, Ti}`: バルクアセンブリのための事前計算された形状因子
  * `boundary_assembly_data::VoronoiFVM.AbstractAssemblyData`: 境界アセンブリのための事前計算された形状因子
  * `assembly_type::Symbol`: :edgewise または :cellwise
  * `is_linear::Bool`: システムは線形か？
  * `outflownoderegions::Union{Nothing, SparseArrays.SparseMatrixCSC{Bool, Int64}}`: その領域番号を持つ流出ノード。
  * `generic_matrix_prep::Any`: 一般的な演算子処理のためのスパース行列の色など
  * `generic_matrix_backend::Any`: スパース性検出器のバックエンド
  * `is_complete::Bool`: システムは完了していますか (種情報がコンパイルされていますか)？
