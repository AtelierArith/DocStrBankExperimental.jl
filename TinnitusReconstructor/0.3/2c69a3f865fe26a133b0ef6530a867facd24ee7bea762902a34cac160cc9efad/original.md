```
wav2spect(audio::Matrix{T}; duration = 0.5, fs = 41000.0) where T
```

If `audio` is a `Matrix`, try to convert to a `SampleBuf` first.
