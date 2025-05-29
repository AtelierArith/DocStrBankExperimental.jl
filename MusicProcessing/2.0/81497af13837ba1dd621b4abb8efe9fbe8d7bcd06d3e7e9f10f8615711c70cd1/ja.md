```
mono(audio::SampleBuf{T, N})
```

マルチチャンネルオーディオをシングルチャンネルに変換します。

# 出力

初期サンプルレートを持つSampleBuf{T, 1}としてモノチャンネルオーディオを返します。

# 引数

## `audio`

シングルチャンネルオーディオに変換されるSampleBuf{T, N}型のオーディオ。

# 例

```julia
using MusicProcessing

audio_one_channel = SampleBuf(rand(1000), 10)
audio_two_channel = SampleBuf(rand(1000, 2), 10)
audio_multi_channel = SampleBuf(rand(1000, 4), 10)

mono(audio_one_channel)
mono(audio_two_channel)
mono(audio_multi_channel)
```
