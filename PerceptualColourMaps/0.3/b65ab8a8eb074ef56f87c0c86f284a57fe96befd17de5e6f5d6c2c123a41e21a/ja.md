applycolormap: 単一チャンネル画像にカラーマップを適用してRGB結果を得る

```
Usage: rgbimg = applycolormap(img, cmap, rnge)

Arguments:  img - カラーマップを適用する単一チャンネル画像。
                  ::ImageMeta{T,2} または ::Array{Float64,2}
           cmap - cmap() によって生成されたRGBカラーマップ。
                  ::Array{ColorTypes.RGBA{Float64},1}
           rnge - カラーマップ全体にマッピングされる画像内の最小値と最大値を指定するオプションの2ベクトル。
                  この範囲外の値はカラーマップの端点にマッピングされます。範囲が省略された場合は
                  画像値の全範囲が使用されます。

Returns: rgbimg - 0-1の範囲の浮動小数点値を持つRGB画像。
                  入力画像のNaN値は黒としてレンダリングされます。
                  ::ImageMeta{Float64,3} または ::Array{Float64,3}

完全なドキュメントについてはapplycolourmapを参照してください
                                    ^
```

関連情報: cmap, applycycliccolourmap, applydivergingcolourmap
