```
Colorbar(parent; kwargs...)
Colorbar(parent, plotobject; kwargs...)
Colorbar(parent, heatmap::Heatmap; kwargs...)
Colorbar(parent, contourf::Contourf; kwargs...)
```

`parent`にColorbarを追加します。`plotobject`、`heatmap`、または`contourf`を渡すと、Colorbarは自動的に設定され、これらのオブジェクトの関連属性（`colormap`、`colorrange`、`highclip`、`lowclip`など）を追跡します。これらの属性を後で調整したい場合は、プロットオブジェクト内で変更してください。そうしないと、Colorbarとプロットオブジェクトの同期が取れなくなります。

Colorbarには以下の属性があります：

`alignmode` デフォルト: `Inside()` 親のGridLayout内でのcolorbarの整列モード。

`bottomspinecolor` デフォルト: `RGBf0(0, 0, 0)` 下部スパインの色。

`bottomspinevisible` デフォルト: `true` 下部スパインが表示されるかどうかを制御します。

`colormap` デフォルト: `lift_parent_attribute(scene, :colormap, :viridis)` Colorbarが使用するカラーマップ。

`flip_vertical_label` デフォルト: `false` 軸が垂直の場合、colorbarラベルを反転します。

`flipaxis` デフォルト: `true` 垂直の場合は右に、水平の場合は上に軸を反転します。

`halign` デフォルト: `:center` 提案されたバウンディングボックス内でのcolorbarの水平整列。

`height` デフォルト: `AbstractPlotting.automatic` Colorbarの高さ設定。

`highclip` デフォルト: `nothing` 高クリップ三角形の色。

`label` デフォルト: `""` カラーバーラベル文字列。

`labelcolor` デフォルト: `lift_parent_attribute(scene, :textcolor, :black)` ラベルの色。

`labelfont` デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")` ラベルのフォントファミリー。

`labelpadding` デフォルト: `5.0` ラベルと目盛りの間の隙間。

`labelsize` デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)` ラベルのフォントサイズ。

`labelvisible` デフォルト: `true` ラベルが表示されるかどうかを制御します。

`leftspinecolor` デフォルト: `RGBf0(0, 0, 0)` 左側スパインの色。

`leftspinevisible` デフォルト: `true` 左側スパインが表示されるかどうかを制御します。

`limits` デフォルト: `(0.0f0, 1.0f0)` Colorbarに描かれる値の範囲。

`lowclip` デフォルト: `nothing` 低クリップ三角形の色。

`minortickalign` デフォルト: `0.0` 軸スパイン上のマイナー目盛りの整列。

`minortickcolor` デフォルト: `:black` マイナー目盛りの目盛り色。

`minorticks` デフォルト: `IntervalsBetween(5)` マイナー目盛りの目盛りロケーター。

`minorticksize` デフォルト: `4.0` マイナー目盛りの目盛りサイズ。

`minorticksvisible` デフォルト: `false` マイナー目盛りが表示されるかどうかを制御します。

`minortickwidth` デフォルト: `1.0` マイナー目盛りの目盛り幅。

`nsteps` デフォルト: `100` Colorbarグラデーションの基盤となるヒートマップのステップ数。

`rightspinecolor` デフォルト: `RGBf0(0, 0, 0)` 右側スパインの色。

`rightspinevisible` デフォルト: `true` 右側スパインが表示されるかどうかを制御します。

`scale` デフォルト: `identity` 軸スケール。

`size` デフォルト: `16` Colorbarの幅または高さ（垂直または水平に応じて）。`width` / `height`で上書きされない限り。

`spinewidth` デフォルト: `1.0` スパインの線幅。

`tellheight` デフォルト: `true` 親レイアウトがこの要素の高さに調整できるかどうかを制御します。

`tellwidth` デフォルト: `true` 親レイアウトがこの要素の幅に調整できるかどうかを制御します。

`tickalign` デフォルト: `0.0` 軸スパインに対する目盛りマークの整列（0 = 外側、1 = 内側）。

`tickcolor` デフォルト: `RGBf0(0, 0, 0)` 目盛りマークの色。

`tickformat` デフォルト: `AbstractPlotting.automatic` 目盛りのフォーマット。

`ticklabelalign` デフォルト: `AbstractPlotting.automatic` 目盛りラベルの水平および垂直整列。

`ticklabelcolor` デフォルト: `lift_parent_attribute(scene, :textcolor, :black)` 目盛りラベルの色。

`ticklabelfont` デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")` 目盛りラベルのフォントファミリー。

`ticklabelpad` デフォルト: `3.0` 目盛りラベルと目盛りマークの間の隙間。

`ticklabelrotation` デフォルト: `0.0` 目盛りラベルの回転。

`ticklabelsize` デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)` 目盛りラベルのフォントサイズ。

`ticklabelspace` デフォルト: `AbstractPlotting.automatic` 目盛りラベルのために予約されたスペース。

`ticklabelsvisible` デフォルト: `true` 目盛りラベルが表示されるかどうかを制御します。

`ticks` デフォルト: `AbstractPlotting.automatic` 目盛り。

`ticksize` デフォルト: `6.0` 目盛りマークのサイズ。

`ticksvisible` デフォルト: `true` 目盛りマークが表示されるかどうかを制御します。

`tickwidth` デフォルト: `1.0` 目盛りマークの線幅。

`topspinecolor` デフォルト: `RGBf0(0, 0, 0)` 上部スパインの色。

`topspinevisible` デフォルト: `true` 上部スパインが表示されるかどうかを制御します。

`valign` デフォルト: `:center` 提案されたバウンディングボックス内でのcolorbarの垂直整列。

`vertical` デフォルト: `true` Colorbarが垂直に配置されるかどうかを制御します。

`width` デフォルト: `AbstractPlotting.automatic` Colorbarの幅設定。Colorbarの向きに対して幅または高さを設定するには`size`を使用してください。
