ternaryimage:  知覚的に均一な3バンドデータからの三元画像

この関数は、明度が密接に一致する3つの基礎色を使用して三元画像を生成します。これらの二次色も同様です。色はRGBの原色ほど鮮やかではありませんが、チャンネル-色の割り当ての順列に関係なく、一貫した特徴の顕著性を持つ三元画像を生成します。これは、緑にエンコードされるチャンネルが知覚結果を支配するRGB原色を使用して構築された三元画像とは対照的です。

Landsat画像や放射計画像に便利です。

```
Usage: rgbimg = ternaryimage(img; bands, histcut, RGB)

Argument:
            img - 少なくとも3つのバンドを持つマルチバンド画像。
                  ::ImageMeta{T,3} または ::Array{T<:Real,3}

Keyword Arguments:
          bands - 赤、緑、青の基礎色マップに割り当てるバンドを示す3つの値の配列。
                  省略した場合、bandsは[1, 2, 3]にデフォルト設定されます。
        histcut - クリップする画像バンドヒストグラムのパーセンテージ。
                  1-2%をクリップするのが有用です。三元画像に白が多く見える場合は、
                  クリップしすぎています。デフォルトは0です。
            RGB - ブールフラグ。trueに設定すると、明度が一致した原色ではなく、
                  古典的なRGB原色を使用して三元画像が構築されます。デフォルトはfalseです。

Returns:
          rgbimg - RGB三元画像
                  ::ImageMeta{T,3} または ::Array{T<:Real,3}
```

3つの原色の導出については、Peter Kovesiの「Good Colour Maps: How to Design Them」を参照してください。arXiv:1509.03700 [cs.GR] 2015。

関連情報: applycolourmap, linearrgbmap
