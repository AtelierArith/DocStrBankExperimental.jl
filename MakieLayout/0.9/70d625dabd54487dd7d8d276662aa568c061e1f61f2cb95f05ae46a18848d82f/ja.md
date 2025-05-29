LAxis には以下の属性があります：

`alignmode`   デフォルト: `Inside()`   親 GridLayout 内の軸の整列モード。

`aspect`   デフォルト: `nothing`   軸の強制アスペクト比。`nothing` は軸を制約なしにし、`DataAspect()` は x 軸と y 軸のデータ制限間の比率と同じ比率を強制し、`AxisAspect(ratio)` は手動比率を設定します。

`autolimitaspect`   デフォルト: `nothing`   データアスペクト比を制約します（`nothing` は比率を制約なしにします）。

`backgroundcolor`   デフォルト: `:white`   軸の背景色。

`bottomspinecolor`   デフォルト: `:black`   下軸スパインの色。

`bottomspinevisible`   デフォルト: `true`   下軸スパインが表示されるかどうかを制御します。

`flip_ylabel`   デフォルト: `false`   ylabel の回転が反転するかどうかを制御します。

`halign`   デフォルト: `:center`   提案されたバウンディングボックス内の軸の水平整列。

`height`   デフォルト: `nothing`   軸の高さ。

`leftspinecolor`   デフォルト: `:black`   左軸スパインの色。

`leftspinevisible`   デフォルト: `true`   左軸スパインが表示されるかどうかを制御します。

`panbutton`   デフォルト: `AbstractPlotting.Mouse.right`   パン用のボタン。

`rightspinecolor`   デフォルト: `:black`   右軸スパインの色。

`rightspinevisible`   デフォルト: `true`   右軸スパインが表示されるかどうかを制御します。

`spinewidth`   デフォルト: `1.0`   軸スパインの幅。

`targetlimits`   デフォルト: `BBox(0, 100, 0, 100)`   説明なし

`tellheight`   デフォルト: `true`   親レイアウトがこの要素の高さに調整できるかどうかを制御します。

`tellwidth`   デフォルト: `true`   親レイアウトがこの要素の幅に調整できるかどうかを制御します。

`title`   デフォルト: `" "`   軸のタイトル文字列。

`titlealign`   デフォルト: `:center`   タイトルの水平整列。

`titlefont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   タイトルのフォントファミリー。

`titlegap`   デフォルト: `10.0`   軸とタイトルの間の隙間。

`titlesize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 20.0f0)`   タイトルのフォントサイズ。

`titlevisible`   デフォルト: `true`   タイトルが表示されるかどうかを制御します。

`topspinecolor`   デフォルト: `:black`   上軸スパインの色。

`topspinevisible`   デフォルト: `true`   上軸スパインが表示されるかどうかを制御します。

`valign`   デフォルト: `:center`   提案されたバウンディングボックス内の軸の垂直整列。

`width`   デフォルト: `nothing`   軸の幅。

`xautolimitmargin`   デフォルト: `(0.05f0, 0.05f0)`   x 方向のオートリミットに追加される相対マージン。

`xaxisposition`   デフォルト: `:bottom`   x 軸の位置（`:bottom` または `:top`）。

`xgridcolor`   デフォルト: `RGBAf0(0, 0, 0, 0.1)`   x グリッド線の色。

`xgridstyle`   デフォルト: `nothing`   x グリッド線の線スタイル。

`xgridvisible`   デフォルト: `true`   x グリッド線が表示されるかどうかを制御します。

`xgridwidth`   デフォルト: `1.0`   x グリッド線の幅。

`xlabel`   デフォルト: `" "`   xlabel 文字列。

`xlabelcolor`   デフォルト: `RGBf0(0, 0, 0)`   xlabel の色。

`xlabelfont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   xlabel のフォントファミリー。

`xlabelpadding`   デフォルト: `15.0`   xlabel と目盛りまたは軸の間のパディング。

`xlabelsize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 20.0f0)`   xlabel のフォントサイズ。

`xlabelvisible`   デフォルト: `true`   xlabel が表示されるかどうかを制御します。

`xpankey`   デフォルト: `AbstractPlotting.Keyboard.x`   x 方向のパンを制限するためのキー。

`xpanlock`   デフォルト: `false`   x 方向のインタラクティブなパンをロックします。

`xreversed`   デフォルト: `false`   x 軸が右方向（false）または左方向（true）に進むかどうかを制御します。

`xtickalign`   デフォルト: `0.0`   軸スパインに対する xtick マークの整列（0 = 外側、1 = 内側）。

`xtickcolor`   デフォルト: `RGBf0(0, 0, 0)`   xtick マークの色。

`xtickformat`   デフォルト: `AbstractPlotting.automatic`   xticks のフォーマット。

`xticklabelalign`   デフォルト: `(:center, :top)`   xticklabels の水平および垂直整列。

`xticklabelcolor`   デフォルト: `RGBf0(0, 0, 0)`   xticklabels の色。

`xticklabelfont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   xticklabels のフォントファミリー。

`xticklabelpad`   デフォルト: `5.0`   xticks と xticklabels の間のスペース。

`xticklabelrotation`   デフォルト: `0.0`   xticklabels の反時計回りの回転（ラジアン）。

`xticklabelsize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 20.0f0)`   xticklabels のフォントサイズ。

`xticklabelspace`   デフォルト: `AbstractPlotting.automatic`   xticklabels のために予約されたスペース。

`xticklabelsvisible`   デフォルト: `true`   xticklabels が表示されるかどうかを制御します。

`xticks`   デフォルト: `AbstractPlotting.automatic`   xticks。

`xticksize`   デフォルト: `10.0`   xtick マークのサイズ。

`xticksvisible`   デフォルト: `true`   xtick マークが表示されるかどうかを制御します。

`xtickwidth`   デフォルト: `1.0`   xtick マークの幅。

`xtrimspine`   デフォルト: `false`   x スパインが最も外側の目盛りに制限されるかどうかを制御します。

`xzoomkey`   デフォルト: `AbstractPlotting.Keyboard.x`   x 方向のズームを制限するためのキー。

`xzoomlock`   デフォルト: `false`   x 方向のインタラクティブなズームをロックします。

`yautolimitmargin`   デフォルト: `(0.05f0, 0.05f0)`   y 方向のオートリミットに追加される相対マージン。

`yaxisposition`   デフォルト: `:left`   y 軸の位置（`:left` または `:right`）。

`ygridcolor`   デフォルト: `RGBAf0(0, 0, 0, 0.1)`   y グリッド線の色。

`ygridstyle`   デフォルト: `nothing`   y グリッド線の線スタイル。

`ygridvisible`   デフォルト: `true`   y グリッド線が表示されるかどうかを制御します。

`ygridwidth`   デフォルト: `1.0`   y グリッド線の幅。

`ylabel`   デフォルト: `" "`   ylabel 文字列。

`ylabelcolor`   デフォルト: `RGBf0(0, 0, 0)`   ylabel の色。

`ylabelfont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   ylabel のフォントファミリー。

`ylabelpadding`   デフォルト: `15.0`   ylabel と目盛りまたは軸の間のパディング。

`ylabelsize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 20.0f0)`   ylabel のフォントサイズ。

`ylabelvisible`   デフォルト: `true`   ylabel が表示されるかどうかを制御します。

`ypankey`   デフォルト: `AbstractPlotting.Keyboard.y`   y 方向のパンを制限するためのキー。

`ypanlock`   デフォルト: `false`   y 方向のインタラクティブなパンをロックします。

`yreversed`   デフォルト: `false`   y 軸が上方向（false）または下方向（true）に進むかどうかを制御します。

`ytickalign`   デフォルト: `0.0`   軸スパインに対する ytick マークの整列（0 = 外側、1 = 内側）。

`ytickcolor`   デフォルト: `RGBf0(0, 0, 0)`   ytick マークの色。

`ytickformat`   デフォルト: `AbstractPlotting.automatic`   yticks のフォーマット。

`yticklabelalign`   デフォルト: `(:right, :center)`   yticklabels の水平および垂直整列。

`yticklabelcolor`   デフォルト: `RGBf0(0, 0, 0)`   yticklabels の色。

`yticklabelfont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   yticklabels のフォントファミリー。

`yticklabelpad`   デフォルト: `5.0`   yticks と yticklabels の間のスペース。

`yticklabelrotation`   デフォルト: `0.0`   yticklabels の反時計回りの回転（ラジアン）。

`yticklabelsize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 20.0f0)`   yticklabels のフォントサイズ。

`yticklabelspace`   デフォルト: `AbstractPlotting.automatic`   yticklabels のために予約されたスペース。

`yticklabelsvisible`   デフォルト: `true`   yticklabels が表示されるかどうかを制御します。

`yticks`   デフォルト: `AbstractPlotting.automatic`   yticks。

`yticksize`   デフォルト: `10.0`   ytick マークのサイズ。

`yticksvisible`   デフォルト: `true`   ytick マークが表示されるかどうかを制御します。

`ytickwidth`   デフォルト: `1.0`   ytick マークの幅。

`ytrimspine`   デフォルト: `false`   y スパインが最も外側の目盛りに制限されるかどうかを制御します。

`yzoomkey`   デフォルト: `AbstractPlotting.Keyboard.y`   y 方向のズームを制限するためのキー。

`yzoomlock`   デフォルト: `false`   y 方向のインタラクティブなズームをロックします。
