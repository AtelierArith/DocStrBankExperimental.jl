```
imrotate(img, θ, [indices]; kwargs...) -> imgr
```

画像 `img` を中心点を中心に時計回りに `θ`∈[0,2π) 回転させます。

# 引数

  * `img::AbstractArray`: 回転させる元の画像。
  * `θ::Real`: 時計回りの回転角度。画像を反時計回りに回転させるには、代わりに負の値を使用します。画像を `d` 度回転させるには、式 `θ=d*π/180` を使用します。
  * `indices` (オプション): 出力画像の軸を指定します。デフォルトでは、回転した画像 `imgr` は切り取られず、したがって一般的には `axes(imgr) == axes(img)` は成り立ちません。

# パラメータ

!!! info
    `method` と `fillvalue` の値を構築するには、最初に `Interpolations` パッケージをロードする必要があります。


  * `method::Union{Degree, InterpolationType}`: 使用したい補間方法。デフォルトは `Linear()` です。
  * `fillvalue`: 新しい領域を埋めるために使用される値。可能であればデフォルト値は `NaN` ですが、そうでなければ `0` です。

この関数は `warp` へのシンプルな高レベルインターフェースです。詳細については、[`warp`](@ref) を参照してください。

# 例

```julia
using TestImages, ImageTransformations
img = testimage("cameraman")

# 画像を時計回りに π/4 回転させる
imgr = imrotate(img, π/4) # 出力軸 (-105:618, -105:618)

# 画像を反時計回りに π/4 回転させる
imgr = imrotate(img, -π/4) # 出力軸 (-105:618, -105:618)

# 元の軸を保持する
# これは `@view imrotate(img, π/4)[axes(img)...]` よりも効率的です
imgr = imrotate(img, π/4, axes(img)) # 出力軸 (1:512, 1:512)
```

デフォルトでは、`imrotate` は定数フィル値 (`NaN` または `0`) を使用したバイリニア補間を使用します。例えば、最近傍補間を使用し、新しい領域を白いピクセルで埋めることができます：

```julia
using Interpolations, ImageCore
imrotate(img, π/4, method=Constant(), fillvalue=oneunit(eltype(img)))
```

そして、いくつかのインスピレーションを得て、周期的な値で埋め、新しい出力をタイル状にしてモザイクを作成することもできます：

```julia
using Interpolations, ImageCore
imgr = imrotate(img, π/4, fillvalue = Periodic())
mosaicview([imgr for _ in 1:9]; nrow=3)
```
