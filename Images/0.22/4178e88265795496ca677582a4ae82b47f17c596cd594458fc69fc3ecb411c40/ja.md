```
sum = boxdiff(integral_image, ytop:ybot, xtop:xbot)
sum = boxdiff(integral_image, CartesianIndex(tl_y, tl_x), CartesianIndex(br_y, br_x))
sum = boxdiff(integral_image, tl_y, tl_x, br_y, br_x)
```

積分画像は、画像の長方形のサブセット内のピクセルの合計を効率的に計算するのに役立つデータ構造です。各ピクセルには、その上と左にあるすべてのピクセルの合計が格納されます。ウィンドウの `yrange` と `xrange` が与えられた場合、ウィンドウのサイズに関係なく、積分画像の4つの配列参照を使用して画像内のウィンドウの合計を直接計算できます。積分画像が与えられた場合 -

```
    A - - - - - - B -
    - * * * * * * * -
    - * * * * * * * -
    - * * * * * * * -
    - * * * * * * * -
    - * * * * * * * -
    C * * * * * * D -
    - - - - - - - - -
```

  * で示された領域内のピクセルの合計は S = D + A - B - C で与えられます。
