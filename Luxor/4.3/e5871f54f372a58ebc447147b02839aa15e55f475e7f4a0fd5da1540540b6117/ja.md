```
markcells(t::Union{Tiler, Table}, cells;
    action = :stroke,
    func = nothing)
```

Tiler/Table `t` の `cells` のセルをマークします。

デフォルトでは、現在の設定を使用してセルの周りにボックスが描画され、`action` に従って塗りつぶされるかストロークされます。

`func` キーワードに対して任意の処理を行う関数を提供できます。この関数は、`position`、`width`、`height`、および `number` の4つの引数を受け取る必要があります。

## 例

このコードは、5行6列に30個の円を描画し、番号を付けて4色で順番に色付けします。`getcells()` は Tiler からセルの選択を取得します。

```julia
@draw begin
    fontsize(30)
    #t = Table(5, 6, 60, 60)
    t = Tiler(400, 400, 5, 6)
    markcells(t, getcells(t, 1:30),
        func = (pos, w, h, n) -> begin
            sethue(["red", "green", "blue", "purple"][mod1(n, end)])
            circle(pos, w / 2, :fill)
            sethue("white")
            text(string(n), pos, halign = :center, valign = :middle)
        end)
end
```
