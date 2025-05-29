imdilate - 2D モルフォロジー膨張（膨張）を矩形または八角形の構造要素で行う

```
Usage: dimg = imdilate(img, seType, seSize)

Arguments: img - 膨張する画像
        seType - "rectangle" または "octagon" のいずれかの文字列で、構造要素のタイプを指定します。 "rect" または "oct" に短縮できます。
        seSize - 構造要素のサイズ。
                 seType が 'rect' の場合、seSize は矩形構造要素のサイズを示す2要素ベクトル [rows, cols] であるか、単一の値であれば構造要素は正方形 [seSize x seSize] になります。
                 seType が 'oct' の場合、seSize は八角形構造要素の名目上の半径です。

Returns:  dimg - 膨張された画像。
```

八角形構造要素の半径は、離散的な近似のためにやや名目上のものであることに注意してください。 何かあれば、構造要素は指定されたよりもわずかに大きな半径になる可能性があります。

この関数は、画像のサイズに対して線形時間で実行するために、Marcel van Herk のアルゴリズムを使用しています。構造要素のサイズに関係なく。

他にも imerode()、erode1d()、dilate1d() があります。
