```
speedup(audio::SampleBuf, speed::Real, windowsize::Int = 1024, hopsize::Int = windowsize >> 2; kwargs...)
```

さまざまなパラメータを使用してスピードアップしたオーディオ波形を返します。

# 出力

windowsizeとhopsizeを使用して、SampleBuf{T, N}としてスピードアップしたオーディオ波形を返します。

# 引数

## `audio`

ピッチをシフトするSampleBuf{T, N}型のオーディオ。

## `windowsize`

stftおよびistft関数のウィンドウサイズを定義するために使用されるパラメータ。

## `hopsize`

stft列間のオーディオフレームの数を定義するために使用されるパラメータ。

# 例

```julia
using MusicProcessing

audio_one_channel = SampleBuf(rand(10000), 10)
audio_two_channel = SampleBuf(rand(10000, 2), 10)
audio_multi_channel = SampleBuf(rand(10000, 4), 10)

speedup(audio_one_channel, 2048, 512)
speedup(audio_one_channel, 2048, 512)
speedup(audio_one_channel, 2048, 512)

```
