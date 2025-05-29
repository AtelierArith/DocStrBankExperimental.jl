```
struct bosonImag <: AbstractBosonBath
```

バスの相関関数の虚部 $C^{u=\textrm{I}}$ のためのボソンバス

# フィールド

  * `Comm`  : 結合演算子のためのスーパー演算子（交換子）。
  * `anComm`  : 結合演算子のためのスーパー演算子（反交換子）。
  * `dimensions` : 結合演算子の次元リスト（システムの次元と等しい必要があります）。
  * `η` : バスの相関関数の虚部 $C^{u=\textrm{I}}$ における係数 $\eta_i$。
  * `γ` : バスの相関関数の虚部 $C^{u=\textrm{I}}$ における係数 $\gamma_i$。
  * `Nterm` : 相関関数の指数展開項の数。

!!! note "`dims` プロパティ"
    与えられた `b::bosonImag` に対して、`b.dims` または `getproperty(b, :dims)` はその `dimensions` を整数ベクトルの型で返します。

