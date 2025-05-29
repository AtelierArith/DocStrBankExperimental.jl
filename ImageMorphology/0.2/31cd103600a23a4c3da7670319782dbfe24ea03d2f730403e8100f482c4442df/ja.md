```
local_minima(image, [maxtree]; connectivity=1) -> Array
```

`image`のすべての*局所最小値*を決定し、ラベル付けします。

# 詳細

*局所最小値*は、同じ値を持ち、その値がセットの直接隣接ピクセルのすべての値よりも小さい接続されたピクセルの集合として定義されます。

技術的には、実装は画像の*最大木*表現に基づいています。最大木がすでに計算されている場合は有益ですが、そうでない場合は[`Images.findlocalminima`](@ref)の方が効率的です。

# 引数

  * `image::GenericGrayImage`: $N$次元の入力画像
  * `connectivity::Integer=1`: 隣接接続性。ピクセルの隣接者に到達するための最大の直交ステップ数。2Dでは、4近傍の場合は1、8近傍の場合は2です。
  * `maxtree::MaxTree`: オプションの事前構築された*最大木*。`maxtree`と`connectivity`のオプションパラメータは相互に排他的であることに注意してください。

# 戻り値

`image`と同じ形状の整数配列。局所最小値でないピクセルは0の値を持ちます。同じ局所最小値のピクセルは同じ正の値（局所最小値ID）を共有します。

# 参照

[`MaxTree`](@ref), [`local_minima!`](@ref), [`local_maxima`](@ref), [`Images.findlocalminima`](@ref)

# 例

`f`を作成します（中心に最小値があり、4つの追加の定数最小値を持つ二次関数）：

```jldoctest; setup = :(using ImageMorphology)
julia> w = 10;

julia> f = [180 + 0.2*((x - w/2)^2 + (y-w/2)^2) for x in 0:w, y in 0:w];

julia> f[3:5, 3:5] .= 40; f[3:5, 8:10] .= 60; f[8:10, 3:5] .= 80; f[8:10, 8:10] .= 100;

julia> f_minima = local_minima(f); # `f`のすべての局所最小値を計算
```

結果の画像には、ラベル付けされた局所最小値が含まれています。
