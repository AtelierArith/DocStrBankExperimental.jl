```
duration(audio::SampleBuf)
```

与えられたオーディオの長さを秒単位で返します。

# 出力

オーディオの長さを（秒単位で）返します。

# 引数

## `audio`

長さを求めるSampleBuf型のオーディオ。

# 例

```julia
using MusicProcessing

audio_one_channel = SampleBuf(rand(1000), 10)
audio_two_channel = SampleBuf(rand(1000, 2), 10)
audio_multi_channel = SampleBuf(rand(1000, 4), 10)

duration(audio_one_channel)
duration(audio_two_channel)
duration(audio_multi_channel)
```
