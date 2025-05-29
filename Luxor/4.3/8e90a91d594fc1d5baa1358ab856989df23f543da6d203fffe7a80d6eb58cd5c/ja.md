```
arrow(start::Point, C1::Point, C2::Point, finish::Point, action=:stroke;
    linewidth       = 1.0,
    arrowheadlength = 10,
    arrowheadangle  = pi/8,
    startarrow      = false,
    finisharrow     = true,
    decoration      = 0.5,
    decorate        = nothing
    arrowheadfunction = nothing)
```

`start` から `finish` まで、制御点 `C1` と `C2` を使ってベジェ曲線の矢印を描きます。矢印の先端は、`startarrow` と `finisharrow` オプションを変更することで追加または非表示にできます。

`decorate` キーワード引数は、矢印のシャフト上の1つ以上の位置でコードを実行できる関数を受け入れます。継承されたグラフィック環境は、スカラーまたはベクトル `decoration` によって与えられたシャフト上の各点で中心に配置され、x軸はその点での曲線の方向に整列します。

### 例

このコードは、オレンジ色で塗りつぶされ、緑色でアウトラインされた矢印の先端を描きます。

```julia
function myarrowheadfunction(originalendpoint, newendpoint, shaftangle)
    @layer begin
        setline(5)
        translate(newendpoint)
        rotate(shaftangle)
        sethue("orange")
        ngon(O, 20, 3, 0, :fill)
        sethue("green")
        ngon(O, 20, 3, 0, :stroke)
    end
end

@drawsvg begin
    background("white")
    arrow(O, 220, 0, π,
        linewidth=10,
        arrowheadlength=30,
        arrowheadangle=π/7,
        clockwise=true,
        arrowheadfunction = myarrowheadfunction)
end
```
