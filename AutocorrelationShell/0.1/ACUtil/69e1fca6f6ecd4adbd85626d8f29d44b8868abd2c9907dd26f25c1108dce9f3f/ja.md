```
makenoisy(x::AbstractArray{<:Number}, rng::MersenneTwister, a::Float64)
```

画像にガウスホワイトノイズを追加します。

# 引数

`x::AbstractArray{<:Number}`: 画像 `rng::MersenneTwister`: 擬似乱数生成器 ex) rng = MersenneTwister(123) `a::Float64`: ノイズのレベルを調整するためのスケーリングパラメータ。

# 例

```julia
using AutocorrelationShell, Images, FileIO, Random

# テスト画像を読み込む
img = load("./test/pictures/boat.jpg")
img = Float64.(Gray.(img))

noisy_image = makenoisy(img, MersenneTwister(123), 0.7)
```
