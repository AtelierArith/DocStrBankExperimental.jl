```julia
curl!(
    curl::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    u::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    v::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    flipsign,
    add,
    kwargs...
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

ベクトル `u, v` のカールが `curl` に書き込まれ、`curl = ∇×(u, v)` となります。`u, v` は 1/coslat スケーリングが含まれていることが期待されており、そうでない場合は `curl` がスケーリングされます。単位球面上で作用し、`radius` キーワード引数が提供されない限り、すべての勾配演算子のように 1/radius スケーリングを省略します。`flipsign` オプションは -∇×(u, v) を計算します。`add` オプションは `curl += ∇×(u, v)` を計算します。`flipsign` と `add` は組み合わせて使用できます。この関数はカーネルを作成するだけで、カールのために反転した u, v -> v, u で一般的な発散関数 _divergence! をその後呼び出します。
