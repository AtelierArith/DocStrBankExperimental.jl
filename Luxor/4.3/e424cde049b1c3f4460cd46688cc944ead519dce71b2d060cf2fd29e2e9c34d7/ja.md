```
dimension(p1::Point, p2::Point;
    format::Function   = (d) -> string(d), # 測定値を文字列に変換する
    offset             = 0.0,              # 左/右、x軸に平行
    fromextension      = (10.0, 10.0),     # 左右の延長線の長さ
    toextension        = (10.0, 10.0),     #
    textverticaloffset = 0.0,              # 範囲 1.0 (上) から -1.0 (下)
    texthorizontaloffset = 0.0,            # 範囲 1.0 (上) から -1.0 (下)
    textgap            = 5,                # 各矢印の開始点間の隙間 (≈ フォントサイズ?)
    textrotation       = 0.0,
    arrowlinewidth     = 1.0,
    arrowheadlength    = 10,
    arrowheadangle     = π/8)
```

`p1` と `p2` の間の距離の寸法グラフィックを計算して描画します。値は `format` 関数でフォーマットできます。

`p1` はページの下側にある点（つまりおそらくy値が高い）、`p2` はページの上側にある点（つまりおそらくy値が低い）です。

`offset` は負のとき左（-x）になります。

寸法グラフィックは `p1` と `p2` の間の線に合わせて回転します。

`textverticaloffset` において、「垂直」と「水平」は、最初の点から2番目の点に沿って「見る」ことによって最もよく理解されます。`textverticaloffset` は -1 から 1 の範囲、`texthorizontaloffset` はデフォルトの単位で表されます。

```
        toextension
        [5  ,  5]
       <---> <--->
                             to
       -----------            +
            ^
            |

           -50

            |
            v
       ----------            +
                            from
       <---> <--->
         [5 , 5]
       fromextension

            <---------------->
                  offset
```

測定された距離とテキストを返します。
