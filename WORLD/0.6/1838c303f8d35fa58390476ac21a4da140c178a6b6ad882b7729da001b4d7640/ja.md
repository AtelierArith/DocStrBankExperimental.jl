```julia
code_aperiodicity(aperiodicity, fs)
code_aperiodicity(aperiodicity, fs, fftsize)

```

CodeAperiodicityは非周期性を符号化します。次元の数はfsによって決まります。

**パラメータ**

  * `aperiodicity` : 符号化前の非周期性
  * `fs` : サンプリング周波数
  * `fftsize` : FFTサイズ（デフォルト : `get_fftsize_for_cheaptrick(fs)`）

**戻り値**

  * `coded_aperiodicity` : 符号化された非周期性
