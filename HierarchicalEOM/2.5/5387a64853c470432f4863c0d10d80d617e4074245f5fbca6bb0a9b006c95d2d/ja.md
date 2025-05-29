```
struct M_Fermion <: AbstractHEOMLSMatrix
```

フェルミオンバスのためのHEOMリウビリアンスーパーオペレーター行列

# フィールド

  * `data<:AbstractSciMLOperator` : HEOMリウビリアンスーパーオペレーターの行列
  * `tier` : フェルミオン階層のためのティア（カットオフレベル）
  * `dimensions` : 結合演算子の次元リスト（システムの次元と等しい必要があります）。
  * `N` : 総ADOの数
  * `sup_dim` : システムスーパーオペレーターの次元
  * `parity` : HEOMLSが作用する演算子のパリティラベル（通常は`EVEN`、フェルミオンシステムのスペクトルを計算するためにのみ`ODD`として設定されます）。
  * `bath::Vector{FermionBath}` : すべての`FermionBath`オブジェクトを格納するベクター
  * `hierarchy::HierarchyDict`: フェルミオン-バス-ADO階層のためのすべての辞書を含むオブジェクト。

!!! note "`dims` プロパティ"
    与えられた `M::M_Fermion` に対して、`M.dims` または `getproperty(M, :dims)` はその `dimensions` を整数ベクターの型で返します。

