```
periodic_derivative_operator(source::LanczosLowNoise;
                             derivative_order = 1,
                             accuracy_order,
                             stencil_width = accuracy_order + 3,
                             xmin, xmax, N,
                             mode = FastMode())
```

`xmin`と`xmax`の間の均一グリッド上で`derivative_order`-th導関数を近似する`PeriodicDerivativeOperator`を作成します。`N`グリッドポイントで、精度の順序`accuracy_order`まで、`stencil_width`は有限差分ステンシルに使用されるノードの数を決定します。導関数の評価は、`mode = ThreadedMode()`を選択することでスレッドを使用して並列化できます。

## 例

```jldoctest
julia> D = periodic_derivative_operator(LanczosLowNoise();
                                        accuracy_order = 2,
                                        xmin = 0.0, xmax = 1.0, N = 10)
周期的な1次導関数演算子の順序2が[0.0, 1.0]のグリッド上で10ノードを使用して、
左に2ノード、右に2ノードのステンシルと、Holoborodko (2008)の係数を使用しています。
  Smooth Noise Robust Differentiators.
  http://www.holoborodko.com/pavel/numerical-methods/numerical-derivative/lanczos-low-Noise-differentiators/

julia> Matrix(D)
10×10 Matrix{Float64}:
  0.0   1.0   2.0   0.0   0.0   0.0   0.0   0.0  -2.0  -1.0
 -1.0   0.0   1.0   2.0   0.0   0.0   0.0   0.0   0.0  -2.0
 -2.0  -1.0   0.0   1.0   2.0   0.0   0.0   0.0   0.0   0.0
  0.0  -2.0  -1.0   0.0   1.0   2.0   0.0   0.0   0.0   0.0
  0.0   0.0  -2.0  -1.0   0.0   1.0   2.0   0.0   0.0   0.0
  0.0   0.0   0.0  -2.0  -1.0   0.0   1.0   2.0   0.0   0.0
  0.0   0.0   0.0   0.0  -2.0  -1.0   0.0   1.0   2.0   0.0
  0.0   0.0   0.0   0.0   0.0  -2.0  -1.0   0.0   1.0   2.0
  2.0   0.0   0.0   0.0   0.0   0.0  -2.0  -1.0   0.0   1.0
  1.0   2.0   0.0   0.0   0.0   0.0   0.0  -2.0  -1.0   0.0

julia> D = periodic_derivative_operator(LanczosLowNoise();
                                        accuracy_order = 2,
                                        xmin = 0 // 1, xmax = 1 // 1, N = 10,
                                        stencil_width = 7)
周期的な1次導関数演算子の順序2が[0//1, 1//1]のグリッド上で10ノードを使用して、
左に3ノード、右に3ノードのステンシルと、Holoborodko (2008)の係数を使用しています。
  Smooth Noise Robust Differentiators.
  http://www.holoborodko.com/pavel/numerical-methods/numerical-derivative/lanczos-low-Noise-differentiators/
```
