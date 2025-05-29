```
wav2spect(audio::Matrix{T}; duration = 0.5, fs = 41000.0) where T
```

`audio`が`Matrix`の場合、まず`SampleBuf`に変換しようとします。
