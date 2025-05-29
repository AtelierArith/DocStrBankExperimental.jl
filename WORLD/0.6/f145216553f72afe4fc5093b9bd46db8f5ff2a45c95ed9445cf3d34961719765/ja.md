```julia
code_spectral_envelope(
    spectrogram,
    fs,
    fftsize,
    number_of_dimentions
)

```

CodeSpectralEnvelopeはスペクトルエンベロープをコーディングします。

**パラメータ**

  * `spectrogram` : スペクトログラム（スペクトルエンベロープの時間系列）
  * `fs` : サンプリング周波数
  * `fftsize` : FFTサイズ
  * `number_of_dimentions` : コーディングされたスペクトルエンベロープの次元数

**戻り値**

  * `coded_spectral_envelope` : コーディングされたスペクトルエンベロープ
