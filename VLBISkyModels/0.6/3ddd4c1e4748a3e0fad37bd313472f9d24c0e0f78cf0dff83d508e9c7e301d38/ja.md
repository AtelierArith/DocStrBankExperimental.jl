```
FINUFFTAlg
```

Flatironの非一様FFT FINUFFTを使用して、可視性マップを計算します。

# フィールド

  * `padfac`: 画像をパディングする量
  * `reltol`: NFFTの相対許容誤差（FINUFFT eps）
  * `threads`: 使用するスレッドの数
  * `fftflags`: 内部AbstractFFTに渡されるフラグ。最も速いFFTWはFFTW.MEASUREですが、事前計算に最も時間がかかります。
