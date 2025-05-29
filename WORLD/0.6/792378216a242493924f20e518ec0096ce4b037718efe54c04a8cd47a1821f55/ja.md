```julia
decode_aperiodicity(coded_aperiodicity, fs)
decode_aperiodicity(coded_aperiodicity, fs, fftsize)

```

DecodeAperiodicityはコーディングされた非周期性をデコードします。

**パラメータ**

  * `coded_aperiodicity` : コーディングされた非周期性
  * `fs` : サンプリング周波数
  * `fftsize` : FFTサイズ (デフォルト : `get_fftsize_for_cheaptrick(fs)`)

**戻り値**

  * `aperiodicity` : デコードされた非周期性
