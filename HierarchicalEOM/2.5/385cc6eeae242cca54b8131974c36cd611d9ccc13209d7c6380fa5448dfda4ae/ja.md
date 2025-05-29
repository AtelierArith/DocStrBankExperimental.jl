```
struct bosonRealImag <: AbstractBosonBath
```

実部と虚部のバス相関関数が組み合わさったボソンバス

# フィールド

  * `Comm`  : 結合演算子のためのスーパー演算子（交換子）。
  * `anComm`  : 結合演算子のためのスーパー演算子（反交換子）。
  * `dimensions` : 結合演算子の次元リスト（システムの次元と等しい必要があります）。
  * `η_real` : バス相関関数 $\sum_i \eta_i \exp(-\gamma_i t)$ における係数 $\eta_i$ の実部。
  * `η_imag` : バス相関関数 $\sum_i \eta_i \exp(-\gamma_i t)$ における係数 $\eta_i$ の虚部。
  * `γ` : バス相関関数 $\sum_i \eta_i \exp(-\gamma_i t)$ における係数 $\gamma_i$。
  * `Nterm` : 相関関数の指数展開項の数。

!!! note "`dims` プロパティ"
    与えられた `b::bosonRealImag` に対して、`b.dims` または `getproperty(b, :dims)` はその `dimensions` を整数ベクトルの型で返します。

