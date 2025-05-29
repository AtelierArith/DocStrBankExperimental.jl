```
struct M_Boson <: AbstractHEOMLSMatrix
```

ボソンバスのためのHEOMリウビリアンスーパーオペレーター行列

# フィールド

  * `data<:AbstractSciMLOperator` : HEOMリウビリアンスーパーオペレーターの行列
  * `tier` : ボソン階層のためのティア（カットオフレベル）
  * `dimensions` : 結合演算子の次元リスト（システムの次元と等しい必要があります）。
  * `N` : 総ADOの数
  * `sup_dim` : システムスーパーオペレーターの次元
  * `parity` : HEOMLSが作用する演算子のパリティラベル（通常は`EVEN`、フェルミオンシステムのスペクトルを計算するためにのみ`ODD`として設定されます）。
  * `bath::Vector{BosonBath}` : すべての`BosonBath`オブジェクトを格納するベクター
  * `hierarchy::HierarchyDict`: ボソンバス-ADO階層のためのすべての辞書を含むオブジェクト。

!!! note "`dims`プロパティ"
    与えられた`M::M_Boson`に対して、`M.dims`または`getproperty(M, :dims)`はその`dimensions`を整数ベクターの型で返します。

