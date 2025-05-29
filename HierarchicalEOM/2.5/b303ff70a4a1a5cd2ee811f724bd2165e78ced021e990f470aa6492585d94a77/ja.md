```
struct HEOMSuperOp
```

一般的なHEOMスーパー演算子行列。  

# フィールド

  * `data` : HEOMスーパー演算子行列
  * `dimensions` : 結合演算子の次元リスト（システムの次元と等しい必要があります）。
  * `N` : 補助密度演算子の数
  * `parity`: パリティラベル（`EVEN`または`ODD`）。

!!! note "`dims` プロパティ"
    与えられた `M::HEOMSuperOp` に対して、`M.dims` または `getproperty(M, :dims)` はその `dimensions` を整数ベクトルの型で返します。

