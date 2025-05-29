```
struct bosonReal <: AbstractBosonBath
```

バスの相関関数の実部 $C^{u=\textrm{R}}$ のためのボソンバス

# フィールド

  * `Comm`  : 結合演算子のためのスーパー演算子（交換子）。
  * `dimensions` : 結合演算子の次元リスト（システムの次元と等しい必要があります）。
  * `η` : バスの相関関数の実部 $C^{u=\textrm{R}}$ における係数 $\eta_i$。
  * `γ` : バスの相関関数の実部 $C^{u=\textrm{R}}$ における係数 $\gamma_i$。
  * `Nterm` : 相関関数の指数展開項の数。

!!! note "`dims` プロパティ"
    与えられた `b::bosonReal` に対して、`b.dims` または `getproperty(b, :dims)` はその `dimensions` を整数ベクトルの型で返します。

