```
pitchshift(audio::SampleBuf{T, N}, semitones::Real = 8)
```

ピッチシフトされたオーディオ波形を返します

# 出力

ピッチシフトされたオーディオ波形を SampleBuf{T, N} として返します。

# 引数

## `audio`

ピッチをシフトする SampleBuf{T, N} 型のオーディオ。

## `semitones`

オーディオの新しいサンプルレートを定義するために使用されるパラメータ。

`new samplerate` = 2.0 ^ (semitones / 12.0)

# 例

```julia
using MusicProcessing

audio_one_channel = SampleBuf(rand(10000), 10)
audio_two_channel = SampleBuf(rand(10000, 2), 10)
audio_multi_channel = SampleBuf(rand(10000, 4), 10)

pitchshift(audio_one_channel, 8)
pitchshift(audio_two_channel, 8)
pitchshift(audio_multi_channel, 8)

```
