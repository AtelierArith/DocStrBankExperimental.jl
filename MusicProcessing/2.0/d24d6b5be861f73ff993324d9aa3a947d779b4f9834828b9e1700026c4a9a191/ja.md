```
zero_crossing_rate(audio::SampleBuf{T, 1}, framesize::Int = 1024, hopsize::Int = framesize >> 2)
```

オーディオ波形のゼロ交差率を返します

# 出力

選択したオーディオの軸に沿ったゼロ交差の配列を、さまざまなパラメータを使用して返します

# 引数

## `audio`

速度を遅くするタイプのSampleBuf{T, N}のオーディオ。

## `framesize`

ゼロ交差の数を計算するためにフレームサイズを定義するために使用されるパラメータ。

## `hopsize`

フレームサイズの列の間のフレームの数を定義するために使用されるパラメータ。

# 例

```julia
using MusicProcessing

audio_one_channel = SampleBuf(rand(10000), 10)

zero_crossing_rate(audio_one_channel, 2048, 512)
```
