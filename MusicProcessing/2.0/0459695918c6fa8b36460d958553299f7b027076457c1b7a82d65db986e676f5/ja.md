```
resample(audio::SampleBuf{T, 2}, samplerate::Real)
```

指定されたサンプルレートで入力オーディオをリサンプリングします。

# 出力

与えられたサンプルレートでリサンプリングされたオーディオをSampleBuf{T, 2}として返します。

# 引数

## `audio`

リサンプリングされるSampleBuf{T, 2}型のオーディオ。

## `samplerate`

最終出力のサンプルレートを指定するためのパラメータ。

# 例

```julia
using MusicProcessing

audio_two_channel = SampleBuf(rand(1000, 2), 10)

resample(audio_two_channel, 5)
```
