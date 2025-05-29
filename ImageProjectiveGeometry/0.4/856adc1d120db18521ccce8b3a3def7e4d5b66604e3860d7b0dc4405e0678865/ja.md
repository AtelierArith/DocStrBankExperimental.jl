imerode - 2D形態学的侵食、矩形または八角形の構造要素を使用

```
Usage: eimg = imerode(img, seType, seSize)

Arguments: img - 侵食される画像
        seType - "rectangle" または "octagon" のいずれかの文字列で、構造要素のタイプを指定します。 "rect" または "oct" に短縮できます。
        seSize - 構造要素のサイズ。
                 seType が 'rect' の場合、seSize は矩形構造要素のサイズを示す2要素ベクトル [rows, cols] であるか、単一の値であれば構造要素は正方形 [seSize x seSize] になります。
                 seType が 'oct' の場合、seSize は八角形構造要素の名目上の半径です。

Returns:  eimg - 侵食された画像。
```

八角形構造要素の半径は、離散的な近似のため、やや名目上のものであることに注意してください。 何かあれば、構造要素は指定されたよりもわずかに大きい半径になる可能性があります。

この関数は、画像のサイズに対して線形時間で実行されるMarcel van Herkのアルゴリズムを使用しており、構造要素のサイズに関係なく動作します。

他にも imdilate()、erode1d()、dilate1d() を参照してください。
