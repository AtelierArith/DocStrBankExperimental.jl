```julia
divergence!(
    div::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    u::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    v::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    flipsign,
    add,
    kwargs...
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

ベクトル `u, v` の発散を `div` に書き込みます、`div = ∇⋅(u, v)`。 `u, v` は 1/coslat スケーリングが含まれていることが期待されます。そうでない場合、`div` はスケーリングされます。単位球体上で作用し、すべての勾配演算子と同様に 1/radius スケーリングを省略します。`radius` キーワード引数が提供されない限り。`flipsign` オプションは -∇⋅(u, v) を計算します。`add` オプションは `div += ∇⋅(u, v)` を計算します。`flipsign` と `add` は組み合わせることができます。この関数はカーネルを作成するだけで、一般的な発散関数 _divergence! をその後呼び出します。
