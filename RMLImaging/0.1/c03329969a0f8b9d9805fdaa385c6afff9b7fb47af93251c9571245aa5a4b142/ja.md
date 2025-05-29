```
SingleNFFT2D(nfft_fwd, nfft_adj, vnorm) <: FourierTransform2D
```

NFFTを使用した単一2D画像のフーリエ変換演算子。

# フィールド

  * `nfft_fwd`: 前方変換のためのNFFT演算子
  * `nfft_adj`: 隣接変換のためのNFFT演算子
  * `Vkernel`: 前方変換された可視性に掛けられる因子（位相シフト、パルス関数、カーネルなど）。
