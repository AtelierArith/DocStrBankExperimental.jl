```
struct M_Boson_Fermion <: AbstractHEOMLSMatrix
```

混合（ボソンおよびフェルミオン）バスのためのHEOMリウビリアンスーパーオペレーター行列

# フィールド

  * `data<:AbstractSciMLOperator` : HEOMリウビリアンスーパーオペレーターの行列
  * `Btier` : ボソン階層のためのティア（カットオフレベル）
  * `Ftier` : フェルミオン階層のためのティア（カットオフレベル）
  * `dimensions` : 結合演算子の次元リスト（システムの次元と等しい必要があります）。
  * `N` : 総ADOの数
  * `sup_dim` : システムスーパーオペレーターの次元
  * `parity` : HEOMLSが作用する演算子のパリティラベル（通常は`EVEN`、フェルミオンシステムのスペクトルを計算するためにのみ`ODD`として設定されます）。
  * `Bbath::Vector{BosonBath}` : すべての`BosonBath`オブジェクトを格納するベクター
  * `Fbath::Vector{FermionBath}` : すべての`FermionBath`オブジェクトを格納するベクター
  * `hierarchy::MixHierarchyDict`: 混合バスADO階層のためのすべての辞書を含むオブジェクト。

!!! note "`dims` プロパティ"
    与えられた `M::M_Boson_Fermion` に対して、`M.dims` または `getproperty(M, :dims)` はその `dimensions` を整数ベクターの型で返します。

