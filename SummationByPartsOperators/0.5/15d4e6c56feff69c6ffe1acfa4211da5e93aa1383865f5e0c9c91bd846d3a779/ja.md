```
periodic_derivative_operator(derivative_order, accuracy_order,
                             xmin, xmax, N,
                             left_offset=-(accuracy_order+1)÷2,
                             mode=FastMode())
periodic_derivative_operator(; derivative_order, accuracy_order,
                             xmin, xmax, N,
                             left_offset=-(accuracy_order+1)÷2,
                             mode=FastMode())
```

[`PeriodicDerivativeOperator`](@ref) を作成して、`xmin` と `xmax` の間の均一グリッド上で `derivative_order`-th の導関数を、`N` グリッドポイントで、精度の順序 `accuracy_order` まで近似します。使用される最も左のグリッドポイントは `left_offset` によって決定されます。導関数の評価は、`mode=ThreadedMode()` を選択することでスレッドを使用して並列化できます。

## 例

```jldoctest
julia> periodic_derivative_operator(derivative_order=1, accuracy_order=2,
                                    xmin=0.0, xmax=1.0, N=11)
Periodic first-derivative operator of order 2 on a grid in [0.0, 1.0] using 11 nodes,
stencils with 1 nodes to the left, 1 nodes to the right, and coefficients of Fornberg (1998)
  Calculation of Weights in Finite Difference Formulas.
  SIAM Rev. 40.3, pp. 685-691.
```
