medfilt2 - 中央フィルタリングの便利なラッパー。

```
Usage:  medimg = medfilt2(img, h::Int, w::Int)
        medimg = medfilt2(img, h::Int)
        medimg = medfilt2(img, hw::Tuple)

Arguments:   img - 処理される画像、Array{T,2}
            h, w - 中央値を計算する矩形ウィンドウの高さと幅。値は奇数でなければならない。
                   hとwはサイズタプルとして指定することも、単一の値として指定することもでき、その場合wとhは等しくなる。

Returns:  medimg - 中央フィルタリングされた画像。

```
