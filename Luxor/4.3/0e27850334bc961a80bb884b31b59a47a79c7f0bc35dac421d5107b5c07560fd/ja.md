```
arrow(centerpos::Point, radius, startangle, endangle;
    linewidth          = 1.0,
    arrowheadlength    = 10,
    arrowheadangle     = π/8,
    decoration         = 0.5,
    decorate           = nothing,
    arrowheadfunction  = nothing,
    clockwise          = true)
```

`centerpos`を中心とし、`startangle`から`endangle`までの弧を描く曲線矢印を描き、端に矢じりを付けます。角度は正のx軸から時計回りに測定されます。

矢印は現在の線幅設定（`setline()`）を使用しません。線幅を指定できます。

`decorate`キーワード引数は、矢印のシャフト上の1つ以上の位置でコードを実行できるゼロ引数関数を受け入れます。継承されたグラフィック環境は、スカラーまたはベクター`decoration`によって与えられた0から1の間のシャフト上の点に中心が置かれ、x軸はその点での曲線の方向に整列します。

デフォルトでは三角形の矢じりが描かれます。しかし、3つの引数（シャフトの端、矢じりの端、シャフトの角度）を受け入れる関数を`arrowheadfunction`キーワード引数に渡すことで、任意の形状の矢じりを描くことができます。
