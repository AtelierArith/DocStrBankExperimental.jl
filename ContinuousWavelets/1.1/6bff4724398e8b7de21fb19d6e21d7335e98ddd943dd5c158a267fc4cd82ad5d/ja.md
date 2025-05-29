```
wavelet(wave::ContWaveClass; Q=8, boundary::WaveletBoundary=DEFAULT_BOUNDARY,
averagingType::Average = Father(), averagingLength = 4,
frameBound=1, p=Inf, β=4, kwargs...)
```

`CWT`型のコンストラクタで、位置引数ではなくキーワード引数を使用しています。
