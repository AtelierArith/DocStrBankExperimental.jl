```
imrotate(img, θ, [indices], [degree = Linear()], [fill = NaN]) -> imgr
```

画像 `img` を中心点を中心に時計回りに `θ`∈[0,2π) 回転させます。反時計回りに回転させるには、角度に負の値を指定します。

デフォルトでは、回転された画像 `imgr` は切り取られません。バイリニア補間が使用され、画像の外側の値は可能であれば `NaN` で埋められ、それ以外の場合は `0` で埋められます。

# 例

```julia
julia> img = testimage("cameraman")

# 切り取らずにバイリニア補間で回転
julia> imrotate(img, π/4)

# 切り取ってバイリニア補間で回転
julia> imrotate(img, π/4, axes(img))

# 切り取らずに最近傍補間で回転
julia> imrotate(img, π/4, Constant())

キーワード `method` は、今や Interpolations.jl の任意の InterpolationType または Degree を受け入れます。これは、その次数の BSpline 補間を定義するために使用され、画像回転中に使用される補間方法を設定します。

```

julia

# 切り取らずに線形補間で回転

julia> imrotate(img, π/4, method = Linear())

# 切り取らずに Lanczos4OpenCV 補間で回転

julia> imrotate(img, π/4, method = Lanczos4OpenCV()) ```

関連項目として [`warp`](@ref) を参照してください。
