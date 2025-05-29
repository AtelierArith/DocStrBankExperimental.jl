```
diameter_opening(image, [maxtree]; min_diameter=8, connectivity=1) -> Array
```

`image`の*直径オープニング*を実行します。

*直径オープニング*は、`min_diameter`よりも小さい直径（バウンディングボックスの最も広い次元）を持つ画像のすべての明るい構造を、`image`の*max-tree*表現において、`min_diameter`以上の直径を持つ最初の祖先コンポーネントから取得した暗い値で置き換えます。

この演算子は*バウンディングボックスオープニング*とも呼ばれます。実際には、結果は*形態学的オープニング*に似ていますが、長くて細い構造は削除されません。

# 引数

  * `image::GenericGrayImage`: $N$次元の入力画像
  * `min_diameter::Number=8`: そのまま保持する画像コンポーネントのバウンディングボックスの最も広い次元の最小長さ（ピクセル単位）
  * `connectivity::Integer=1`: 隣接接続性。ピクセルの隣接点に到達するための最大直交ステップ数。2Dでは、4近傍の場合は1、8近傍の場合は2です。
  * `maxtree::MaxTree`: オプションの事前構築された*max-tree*。`maxtree`と`connectivity`のオプションパラメータは相互に排他的であることに注意してください。

# 戻り値

`image`と同じ型と形状の配列。

# 参照

[`diameter_opening!`](@ref), [`diameter_closing`](@ref), [`area_opening`](@ref), [`MaxTree`](@ref), [`opening`](@ref)

# 参考文献

1. Walter, T., & Klein, J.-C. (2002). *Automatic Detection of Microaneurysms in Color Fundus Images of the Human Retina by Means of the Bounding Box Closing*. In A. Colosimo, P. Sirabella, A. Giuliani (Eds.), *Medical Data Analysis. Lecture Notes in Computer Science*, vol 2526, 210-220. Springer Berlin Heidelberg.

    > https://doi.org/10.1007/3-540-36104-9_23
2. Carlinet, E., & Geraud, T. (2014). *A Comparative Review of Component Tree Computation Algorithms*. IEEE Transactions on Image Processing, 23(9), 3885-3895.

    > https://doi.org/10.1109/TIP.2014.2336551

# 例

テスト画像`f`を作成します（中心に最大値があり、4つの追加の局所最大値を持つ二次関数）：

```jldoctest; setup = :(using ImageMorphology)
julia> w = 12;

julia> f = [20 - 0.2*((x - w/2)^2 + (y-w/2)^2) for x in 0:w, y in 0:w];

julia> f[3:4, 2:6] .= 40; f[3:5, 10:12] .= 60; f[10:12, 3:5] .= 80;

julia> f[10:11, 10:12] .= 100; f[11, 11] = 100;

julia> f_dopen = diameter_opening(f, min_diameter=3, connectivity=1);
```

最大直径が2以下のピークは削除されます。残りのピークについては、バウンディングボックスの最も広い側が少なくとも3になります。
