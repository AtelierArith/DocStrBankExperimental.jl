```
slowdown(audio::SampleBuf, ratio::Real, windowsize::Int = 1024, hopsize::Int = windowsize >> 2; kwargs...)
```

さまざまなパラメータを使用して音声をスローダウンします

# 出力

windowsizeとhopsizeを使用して、SampleBuf{T, N}としてスローダウンされた音声波形を返します。

# 引数

## `audio`

スローダウンする音声の型SampleBuf{T, N}。

## `windowsize`

stftおよびistft関数のウィンドウサイズを定義するために使用されるパラメータ。

## `hopsize`

stft列の間のフレーム数を定義するために使用されるパラメータ。

# 例

```julia
using MusicProcessing

audio_one_channel = SampleBuf(rand(10000), 10)
audio_two_channel = SampleBuf(rand(10000, 2), 10)
audio_multi_channel = SampleBuf(rand(10000, 4), 10)

slowdown(audio_one_channel, 2048, 512)
slowdown(audio_two_channel, 2048, 512)
slowdown(audio_multi_channel, 2048, 512)

```
