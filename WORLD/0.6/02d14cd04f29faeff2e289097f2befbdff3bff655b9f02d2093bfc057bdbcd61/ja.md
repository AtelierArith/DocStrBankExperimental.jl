```julia
decode_spectral_envelope(
    coded_spectral_envelope,
    fs,
    fftsize
)

```

DecodeSpectralEnvelopeはスペクトルエンベロープをデコードします。

**パラメータ**

  * `coded_spectral_envelope` : コード化されたスペクトルエンベロープ
  * `fs` : サンプリング周波数
  * `fftsize` : FFTサイズ

**戻り値**

  * `spectrogram` : デコードされたスペクトルエンベロープ
