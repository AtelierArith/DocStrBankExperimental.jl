```
periodic_derivative_operator(source::Holoborodko2008,
                             derivative_order, accuracy_order,
                             xmin, xmax, N; mode=FastMode(), kwargs...)
periodic_derivative_operator(source::Holoborodko2008;
                             derivative_order, accuracy_order,
                             xmin, xmax, N, mode=FastMode(), kwargs...)
```

`derivative_order`-階の導関数を`xmin`と`xmax`の間の均一なグリッド上で`N`のグリッドポイントを用いて、精度の順序`accuracy_order`まで近似する`PeriodicDerivativeOperator`を作成します。使用される最も左のグリッドポイントは`left_offset`によって決定されます。導関数の評価は、`mode=ThreadedMode()`を選択することでスレッドを使用して並列化できます。

## 例

```jldoctest
julia> periodic_derivative_operator(Holoborodko2008(), derivative_order=1, accuracy_order=2,
                                    xmin=0.0, xmax=1.0, N=11)
Periodic first-derivative operator of order 2 on a grid in [0.0, 1.0] using 11 nodes,
stencils with 2 nodes to the left, 2 nodes to the right, and coefficients of   Holoborodko (2008)
  Smooth Noise Robust Differentiators.
  http://www.holoborodko.com/pavel/numerical-methods/numerical-derivative/smooth-low-noise-differentiators/
```
