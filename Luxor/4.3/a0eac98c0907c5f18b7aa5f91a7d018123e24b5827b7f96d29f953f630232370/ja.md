```
arrow(startpoint::Point, endpoint::Point;
    linewidth         = 1.0,
    arrowheadlength   = 10,
    arrowheadangle    = pi/8,
    decoration        = 0.5 or range(),
    decorate          = nothing,
    arrowheadfunction = nothing)
```

2つの点の間に線を描き、端に矢印の頭を追加します。矢印の頭の長さは矢印の頭の側の長さであり、矢印の頭の角度は矢印の頭の傾斜側と矢印のシャフトの間の角度です。

矢印は現在の線幅設定（`setline()`）を使用せず、デフォルトは1ですが、別の値を指定することができます。ストローク/フィリングは必要なく、シャフトはストロークされ、頭は現在の色で塗りつぶされます。

### 装飾

`decorate`キーワード引数は、矢印のシャフト上の1つ以上の位置でコードを実行できる引数なしの関数を受け入れます。継承されたグラフィック環境は、スカラーまたはベクトル`decoration`によって与えられた0から1の間のシャフト上の各点に中心が置かれ、x軸はその点での曲線の方向に整列します。

### 矢印の頭

デフォルトでは三角形の矢印の頭が描かれます。しかし、3つの引数（シャフトの端、矢印の頭の端、シャフトの角度）を受け入れる関数を`arrowheadfunction`キーワード引数に渡すことができます。これにより、任意の形の矢印の頭を描くことができます。

### 例

```julia
function redbluearrow(shaftendpoint, endpoint, shaftangle)
    @layer begin
        sethue("red")
        sidept1 = shaftendpoint  + polar(10, shaftangle + π/2 )
        sidept2 = shaftendpoint  - polar(10, shaftangle + π/2)
        poly([sidept1, endpoint, sidept2], :fill)
        sethue("blue")
        poly([sidept1, endpoint, sidept2], :stroke, close=false)
    end
end

@drawsvg begin
    background("white")
    arrow(O, O + (120, 120),
        linewidth=4,
        arrowheadlength=40,
        arrowheadangle=π/7,
        arrowheadfunction = redbluearrow)

    arrow(O, 100, 3π/2, π,
        linewidth=4,
        arrowheadlength=20,
        clockwise=false,arrowheadfunction=redbluearrow)
end 800 250
```
