stdfilt2 - 画像全体の局所標準偏差を計算します。

```
Usage:  stdimg = stdfilt2(img, h::Int, w::Int)
        stdimg = stdfilt2(img, h::Int)
        stdimg = stdfilt2(img, hw::Tuple)

Arguments:   img - 処理される画像、Array{T,2}
            h, w - 標準偏差を計算するための矩形ウィンドウの高さと幅。値は奇数でなければなりません。
                   hとwはサイズのタプルとして指定することも、単一の値として指定することもでき、その場合wとhは等しくなります。

Returns:  stdimg - 標準偏差画像。

```
