```julia
get_fftsize_for_cheaptrick(fs)
get_fftsize_for_cheaptrick(fs, opt)

```

GetFFTSizeForCheapTrickは、サンプリング周波数とf0の下限に基づいてFFTサイズを計算します（これはworld.hで定義されています）。

**パラメータ**

  * `fs`: サンプリング周波数
  * `opt`: CheapTrickOption

**戻り値**

  * `fftsize` : FFTサイズ
