```
text(x, y, value [,halign::HAlignment [,valign::VAlignment [,rot::Rotation]]])
```

現在のコンテキストに対して位置（`x`,`y`）でテキスト `value` を描画します。

テキストのデフォルトの配置は `hleft` `vbottom` です。垂直および水平方向の配置は、`halign` と `valign` の値としてそれぞれ `hleft`、`hcenter` または `hright` と `vtop`、`vcenter` または `vbottom` を渡すことによって指定されます。
