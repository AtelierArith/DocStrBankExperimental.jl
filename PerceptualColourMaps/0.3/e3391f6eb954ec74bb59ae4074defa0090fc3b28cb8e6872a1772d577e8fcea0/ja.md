applycolourmap/applycolormap: 単一チャネル画像にカラーマップを適用してRGB結果を得る

```
Usage: rgbimg = applycolourmap(img, cmap, rnge)

Arguments:  img - カラーマップを適用する単一チャネル画像。
                  ::ImageMeta{T,2} または ::Array{Float64,2}
           cmap - cmap()によって生成されたRGBカラーマップ。
                  ::Array{ColorTypes.RGBA{Float64},1}
           rnge - カラーマップ全体にマッピングされる画像内の最小値と最大値を指定するオプションの2ベクトル。
                  この範囲外の値はカラーマップの端点にマッピングされます。範囲が省略された場合は
                  画像値の全範囲が使用されます。

Returns: rgbimg - 0-1の範囲の浮動小数点値のRGB画像。
                  入力画像のNaN値は黒にマッピングされます。
                  ::ImageMeta{Float64,3} または ::Array{Float64,3}
```

カラーマップを単に設定するだけでなく、この関数を使用する理由は何ですか？

実際には、applycycliccolourmap()およびapplydivergingcolourmap()関数を使用したいと思うでしょう。これらの関数はこの関数を利用しています。

多くの視覚化パッケージは、カラーマップを適用して画面にレンダリングする前に、データを正規化するためにオフセットを自動的に適用し、例えば0-255の範囲にスケーリングを行うことがあります。多くの場合、これは有用です。しかし、データを発散型または循環型カラーマップでレンダリングしたい場合、この動作は明らかに適切ではありません。なぜなら、これらのタイプのカラーマップは、データ値が何らかの形で尊重される必要があるからです。

この関数は「範囲」パラメータを提供することで、データ値を尊重する方法でカラーマップを適用することを可能にします。

参照: cmap, applycycliccolourmap, applydivergingcolourmap
