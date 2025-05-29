```julia
transform!(
    specs::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    grids::SpeedyWeather.RingGrids.AbstractGridArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

スペクトル変換（グリッドからスペクトル空間へ）は、`grids`のn次元配列から球面調和係数のn次元配列`specs`へと変換します。これは、経度方向でFFTを使用し、緯度方向で対称性を利用してレジェンドル変換を行います。スペクトル変換は数値形式に柔軟ですが、`grids`とスペクトル変換`S`は同じ数値形式である必要があります。これは、SpectralTransform構造体`S`内の事前計算された配列、FFTプラン、およびその他の定数を使用します。スペクトル変換は、`typeof(grids)<:AbstractGridArray`であり、`S.Grid`が一致する限り、グリッドに柔軟です。
