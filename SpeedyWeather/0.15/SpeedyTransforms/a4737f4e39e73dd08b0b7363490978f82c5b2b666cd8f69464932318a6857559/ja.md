```julia
∇²!(
    ∇²alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    add,
    flipsign,
    inverse,
    radius
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

ラプラス演算子 ∇² が球面座標系のスペクトル係数 `alms` に適用されます。固有値は `S` に事前計算されています。∇²! はインプレースバージョンで、出力を最初の引数 `∇²alms` に直接格納します。単位球に作用し、半径スケーリングを省略します。これは、`radius` キーワード引数が提供されない限り、すべてのインプレース勾配演算子に当てはまります。

# キーワード引数

  * `add=true` は ∇²(alms) を出力に加えます
  * `flipsign=true` は -∇²(alms) を代わりに計算します
  * `inverse=true` は ∇⁻²(alms) を代わりに計算します

デフォルトは `add=false`、`flipsign=false`、`inverse=false` です。これらのオプションは組み合わせることができます。
