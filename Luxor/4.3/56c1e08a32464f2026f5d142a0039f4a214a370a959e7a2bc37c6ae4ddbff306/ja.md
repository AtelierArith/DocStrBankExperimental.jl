```
getworldposition(pt::Point = O;
    centered=true)
```

`pt`のワールド座標を返します。

Luxorの描画のデフォルト座標系は、左上隅が0/0です。`origin()`（またはさまざまな`@-`マクロショートカット）を使用すると、すべてが描画の中心に移動し、この関数はデフォルトの`centered`オプションで`origin()`関数を前提とします。`centered=false`を選択すると、返される座標は描画の左上隅に対して相対的になります。

```julia
origin()
translate(120, 120)
@show currentpoint()      # => Point(0.0, 0.0)
@show getworldposition()  # => Point(120.0, 120.0)
```
