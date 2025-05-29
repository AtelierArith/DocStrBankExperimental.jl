```
brush(pt1, pt2, width=10;
    strokes=10,
    minwidth=0.01,
    maxwidth=0.03,
    twist = -1,
    lowhandle  = 0.3,
    highhandle = 0.7,
    randomopacity = true,
    tidystart = false,
    action = :fill,
    strokefunction = (nbpb) -> nbpb))
```

ランダム化された個々の塗りつぶされたベジェパスから構成される合成ブラシストロークを描きます。

`strokefunction` は、ベジェパスセグメントを処理したり、描画される前に他のことを行うための関数を許可します。

!!! note
    この関数には多くのランダム性があります。結果は予測不可能です。

