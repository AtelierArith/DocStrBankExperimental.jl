applydivergingcolourmap/applydivergingcolormap - 画像に発散色マップを適用します

発散色マップでデータを正しく表示するためには、データ値が尊重されることが重要です。そうすることで、データ内の参照値が発散色マップの中心エントリと正しく関連付けられます。

対照的に、デフォルトの表示方法は通常、データ値を直接尊重せず、表示および色マップでのレンダリングの前に不適切なオフセットや正規化を行うことがあります。

```
Usage:  rgbim = applydivergingcolourmap(img, map, refval)

Arguments:
           img - レンダリングされる画像。  ::ImageMeta または ::Array{Float64,2}
           map - データをレンダリングするための色マップ。
        refval - 発散色マップの中心点に関連付けられる参照値。  デフォルトは0。
Returns:
        rgbimg - レンダリングされた画像。
                 ::ImageMeta{Float64,3} または ::Array{Float64,3}
```

生成可能なすべての発散色マップのリストは、cmap()を使用して取得できます: > cmap("div")

関連情報: applycolourmap, applycycliccolourmap
