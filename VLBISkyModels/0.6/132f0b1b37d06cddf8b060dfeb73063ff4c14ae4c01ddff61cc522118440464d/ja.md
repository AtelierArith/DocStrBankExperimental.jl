```
NFFTAlg
```

非一様FFTを使用して可視マップを計算します。オプションで、NFFTを計算するuv位置を渡すことができます。これにより、NFFTプランをキャッシュしてパフォーマンスを向上させることができます。

# フィールド

  * `padfac`: 画像をパディングする量
  * `reltol`: NFFTの相対許容誤差
  * `precompute`: NFFT補間アルゴリズム。
  * `fftflags`: 内部AbstractFFTに渡されるフラグ。最も速いFFTWはFFTW.MEASUREですが、事前計算に最も時間がかかります。
