mapimage2plane! - 3Dの平面に画像を投影します

```
Usage:  mapimage2plane!(mappedimg, rect3Dpts, img, P)

Arguments:
       mappedimg - 結果として得られる投影画像を格納するバッファ。 ::Array{Float64,2}
          rect3D - 画像の長方形の4つのコーナーの3D座標を指定する3x4配列。ポイントは左上隅から時計回りに並べられています。
             img - 投影される画像。 ::Array{Float64,2}
               P - imgのための3x4投影行列。

```

平面の長方形のコーナーを指定する4つの3Dポイントが画像に投影され、それに対応する画像座標が得られます。これらのポイントとmappedimageバッファのコーナー座標との間でホモグラフィーが計算されます。これがimgに適用され、mappedimgに投影されます。
