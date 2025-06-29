```
struct fermionEmit <: AbstractFermionBath
```

フェルミオン系の放出プロセスを相関関数 $C^{\nu=-}$ によって記述するバスオブジェクト

# フィールド

  * `spre`   : 結合演算子のためのスーパー演算子（左側演算子の乗算）。
  * `spost`  : 結合演算子のためのスーパー演算子（右側演算子の乗算）。
  * `spreD`  : 結合演算子の随伴のためのスーパー演算子（左側演算子の乗算）。
  * `spostD` : 結合演算子の随伴のためのスーパー演算子（右側演算子の乗算）。
  * `dimensions` : 結合演算子の次元リスト（システムの次元と等しい必要があります）。
  * `η` : 放出バス相関関数 $C^{\nu=-}$ の係数 $\eta_i$。
  * `γ` : 放出バス相関関数 $C^{\nu=-}$ の係数 $\gamma_i$。
  * `η_absorb` : 吸収バス相関関数 $C^{\nu=+}$ の係数 $\eta_i$。
  * `Nterm` : 相関関数の指数展開項の数。

!!! note "`dims` プロパティ"
    与えられた `b::fermionEmit` に対して、`b.dims` または `getproperty(b, :dims)` はその `dimensions` を整数ベクトルの型で返します。

