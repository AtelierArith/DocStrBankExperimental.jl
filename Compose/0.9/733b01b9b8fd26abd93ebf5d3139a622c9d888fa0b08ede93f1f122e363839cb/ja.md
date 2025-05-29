```
context(x0=0.0w, y0=0.0h, width=1.0w, height=1.0h;
        units=nothing,
        rotation=nothing, mirror=nothing, shear=nothing,
        withjs=false, withoutjs=false,
        minwidth=nothing, minheight=nothing,
        order=0, clip=false, raster=false) -> Context
```

ツリー構造にグラフィックを定義するノードを作成します。子ノードを親ノードに接続するには [`compose`](@ref) を使用します。さらに [`Rotation`](@ref)、[`Mirror`](@ref)、および [`Shear`](@ref) も参照してください。

# 引数

  * `units`: [`UnitBox`](@ref) によって定義されるコンテキストの座標系。
  * `order`: このコンテキストのZオーダー、兄弟ノードに対しての相対的な位置。
  * `clip`: trueの場合、キャンバスのバウンディングボックスで子をクリップします。
  * `withjs`: SVGJSバックエンドに描画していない場合、このコンテキストとその下のすべてを無視します。
  * `withoutjs`: SVGJSバックエンドに描画している場合、このコンテキストを無視します。
  * `raster`: 可能であれば、このサブツリーをビットマップとしてレンダリングします。これにはCairoが必要です。Cairoが利用できない場合、デフォルトのレンダリングが使用されます。
  * `minwidth` および `minheight`: 正しく描画するために必要な最小サイズ（ミリメートル単位）。
