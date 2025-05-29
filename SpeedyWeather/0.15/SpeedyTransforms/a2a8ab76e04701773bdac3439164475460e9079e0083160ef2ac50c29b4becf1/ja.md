```julia
transform!(
    grids::SpeedyWeather.RingGrids.AbstractGridArray,
    specs::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    unscale_coslat
) -> SpeedyWeather.RingGrids.AbstractGridArray

```

球面調和係数のn次元配列`specs`からリンググリッドのn次元配列`grids`へのスペクトル変換（スペクトルからグリッド空間へ）。経度方向にはFFTを、緯度方向には対称性を利用してレジェンドル変換を使用します。スペクトル変換は数値形式に柔軟ですが、`grids`とスペクトル変換`S`は同じ数値形式である必要があります。スペクトル変換構造体`S`内の事前計算された配列、FFTプラン、およびその他の定数を使用します。スペクトル変換は、`typeof(grids)<:AbstractGridArray`であり、`S.Grid`が一致する限り、グリッドに柔軟です。
