Axisには以下の属性があります：

`alignmode`   デフォルト: `Inside()`   親GridLayout内の軸の整列モード。

`aspect`   デフォルト: `nothing`   軸の強制アスペクト比。`nothing`は軸を制約なしにし、`DataAspect()`はx軸とy軸のデータ制限間の比率と同じ比率を強制し、`AxisAspect(ratio)`は手動比率を設定します。

`autolimitaspect`   デフォルト: `nothing`   データアスペクト比を制約します（`nothing`は比率を制約なしにします）。

`backgroundcolor`   デフォルト: `:white`   軸の背景色。

`bottomspinecolor`   デフォルト: `:black`   下部軸スパインの色。

`bottomspinevisible`   デフォルト: `true`   下部軸スパインが表示されるかどうかを制御します。

`flip_ylabel`   デフォルト: `false`   ylabelの回転が反転するかどうかを制御します。

`halign`   デフォルト: `:center`   提案されたバウンディングボックス内の軸の水平整列。

`height`   デフォルト: `nothing`   軸の高さ。

`leftspinecolor`   デフォルト: `:black`   左側軸スパインの色。

`leftspinevisible`   デフォルト: `true`   左側軸スパインが表示されるかどうかを制御します。

`limits`   デフォルト: `(nothing, nothing)`   ユーザーが手動で設定した制限。`reset_limits!`を呼び出すと再設定され、`autolimits!`によってnothingに設定されます。タプル（xlow, xhigh, ylow, high）またはタプル（nothing*or*xlims, nothing*or*ylims）である必要があります。`xlims!`、`ylims!`、および`limits!`によって設定されます。

`palette`   デフォルト: `if scene !== nothing && haskey(scene.attributes, :palette)     deepcopy(scene.palette) else     Attributes() end`   キーごとに1つのパレットを持つ属性、例えば`color = [:red, :green, :blue]`

`panbutton`   デフォルト: `AbstractPlotting.Mouse.right`   パン用のボタン。

`rightspinecolor`   デフォルト: `:black`   右側軸スパインの色。

`rightspinevisible`   デフォルト: `true`   右側軸スパインが表示されるかどうかを制御します。

`spinewidth`   デフォルト: `1.0`   軸スパインの幅。

`tellheight`   デフォルト: `true`   親レイアウトがこの要素の高さに調整できるかどうかを制御します。

`tellwidth`   デフォルト: `true`   親レイアウトがこの要素の幅に調整できるかどうかを制御します。

`title`   デフォルト: `""`   軸のタイトル文字列。

`titlealign`   デフォルト: `:center`   タイトルの水平整列。

`titlecolor`   デフォルト: `lift_parent_attribute(scene, :textcolor, :black)`   タイトルの色。

`titlefont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   タイトルのフォントファミリー。

`titlegap`   デフォルト: `4.0`   軸とタイトルの間の隙間。

`titlesize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)`   タイトルのフォントサイズ。

`titlevisible`   デフォルト: `true`   タイトルが表示されるかどうかを制御します。

`topspinecolor`   デフォルト: `:black`   上部軸スパインの色。

`topspinevisible`   デフォルト: `true`   上部軸スパインが表示されるかどうかを制御します。

`valign`   デフォルト: `:center`   提案されたバウンディングボックス内の軸の垂直整列。

`width`   デフォルト: `nothing`   軸の幅。

`xautolimitmargin`   デフォルト: `(0.05f0, 0.05f0)`   x方向の自動制限に追加される相対的なマージン。

`xaxisposition`   デフォルト: `:bottom`   x軸の位置（`:bottom`または`:top`）。

`xgridcolor`   デフォルト: `RGBAf0(0, 0, 0, 0.12)`   xグリッド線の色。

`xgridstyle`   デフォルト: `nothing`   xグリッド線の線スタイル。

`xgridvisible`   デフォルト: `true`   xグリッド線が表示されるかどうかを制御します。

`xgridwidth`   デフォルト: `1.0`   xグリッド線の幅。

`xlabel`   デフォルト: `""`   xlabel文字列。

`xlabelcolor`   デフォルト: `lift_parent_attribute(scene, :textcolor, :black)`   xlabelの色。

`xlabelfont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   xlabelのフォントファミリー。

`xlabelpadding`   デフォルト: `3.0`   xlabelと目盛りまたは軸の間のパディング。

`xlabelsize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)`   xlabelのフォントサイズ。

`xlabelvisible`   デフォルト: `true`   xlabelが表示されるかどうかを制御します。

`xminorgridcolor`   デフォルト: `RGBAf0(0, 0, 0, 0.05)`   xマイナーグリッド線の色。

`xminorgridstyle`   デフォルト: `nothing`   xマイナーグリッド線の線スタイル。

`xminorgridvisible`   デフォルト: `false`   xマイナーグリッド線が表示されるかどうかを制御します。

`xminorgridwidth`   デフォルト: `1.0`   xマイナーグリッド線の幅。

`xminortickalign`   デフォルト: `0.0`   軸スパイン上のxマイナー目盛りの整列。

`xminortickcolor`   デフォルト: `:black`   xマイナー目盛りの目盛り色。

`xminorticks`   デフォルト: `IntervalsBetween(2)`   xマイナー目盛りの目盛りロケーター。

`xminorticksize`   デフォルト: `4.0`   xマイナー目盛りの目盛りサイズ。

`xminorticksvisible`   デフォルト: `false`   x軸のマイナー目盛りが表示されるかどうかを制御します。

`xminortickwidth`   デフォルト: `1.0`   xマイナー目盛りの目盛り幅。

`xpankey`   デフォルト: `AbstractPlotting.Keyboard.x`   x方向のパンを制限するためのキー。

`xpanlock`   デフォルト: `false`   x方向のインタラクティブなパンをロックします。

`xrectzoom`   デフォルト: `true`   矩形ズームがx次元に影響を与えるかどうかを制御します。

`xreversed`   デフォルト: `false`   x軸が右方向（false）または左方向（true）に進むかどうかを制御します。

`xscale`   デフォルト: `identity`   x軸のスケール。

`xtickalign`   デフォルト: `0.0`   軸スパインに対するxtickマークの整列（0 = 外側、1 = 内側）。

`xtickcolor`   デフォルト: `RGBf0(0, 0, 0)`   xtickマークの色。

`xtickformat`   デフォルト: `AbstractPlotting.automatic`   xticksのフォーマット。

`xticklabelalign`   デフォルト: `AbstractPlotting.automatic`   xticklabelsの水平および垂直整列。

`xticklabelcolor`   デフォルト: `lift_parent_attribute(scene, :textcolor, :black)`   xticklabelsの色。

`xticklabelfont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   xticklabelsのフォントファミリー。

`xticklabelpad`   デフォルト: `2.0`   xticksとxticklabelsの間のスペース。

`xticklabelrotation`   デフォルト: `0.0`   xticklabelsの反時計回りの回転（ラジアン）。

`xticklabelsize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)`   xticklabelsのフォントサイズ。

`xticklabelspace`   デフォルト: `AbstractPlotting.automatic`   xticklabelsのために予約されたスペース。

`xticklabelsvisible`   デフォルト: `true`   xticklabelsが表示されるかどうかを制御します。

`xticks`   デフォルト: `AbstractPlotting.automatic`   xticks。

`xticksize`   デフォルト: `6.0`   xtickマークのサイズ。

`xticksvisible`   デフォルト: `true`   xtickマークが表示されるかどうかを制御します。

`xtickwidth`   デフォルト: `1.0`   xtickマークの幅。

`xtrimspine`   デフォルト: `false`   xスパインが最も外側の目盛りに制限されるかどうかを制御します。

`xzoomkey`   デフォルト: `AbstractPlotting.Keyboard.x`   x方向のズームを制限するためのキー。

`xzoomlock`   デフォルト: `false`   x方向のインタラクティブなズームをロックします。

`yautolimitmargin`   デフォルト: `(0.05f0, 0.05f0)`   y方向の自動制限に追加される相対的なマージン。

`yaxisposition`   デフォルト: `:left`   y軸の位置（`:left`または`:right`）。

`ygridcolor`   デフォルト: `RGBAf0(0, 0, 0, 0.12)`   yグリッド線の色。

`ygridstyle`   デフォルト: `nothing`   yグリッド線の線スタイル。

`ygridvisible`   デフォルト: `true`   yグリッド線が表示されるかどうかを制御します。

`ygridwidth`   デフォルト: `1.0`   yグリッド線の幅。

`ylabel`   デフォルト: `""`   ylabel文字列。

`ylabelcolor`   デフォルト: `lift_parent_attribute(scene, :textcolor, :black)`   ylabelの色。

`ylabelfont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   ylabelのフォントファミリー。

`ylabelpadding`   デフォルト: `5.0`   ylabelと目盛りまたは軸の間のパディング。

`ylabelsize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)`   ylabelのフォントサイズ。

`ylabelvisible`   デフォルト: `true`   ylabelが表示されるかどうかを制御します。

`yminorgridcolor`   デフォルト: `RGBAf0(0, 0, 0, 0.05)`   yマイナーグリッド線の色。

`yminorgridstyle`   デフォルト: `nothing`   yマイナーグリッド線の線スタイル。

`yminorgridvisible`   デフォルト: `false`   yマイナーグリッド線が表示されるかどうかを制御します。

`yminorgridwidth`   デフォルト: `1.0`   yマイナーグリッド線の幅。

`yminortickalign`   デフォルト: `0.0`   軸スパイン上のyマイナー目盛りの整列。

`yminortickcolor`   デフォルト: `:black`   yマイナー目盛りの目盛り色。

`yminorticks`   デフォルト: `IntervalsBetween(2)`   yマイナー目盛りの目盛りロケーター。

`yminorticksize`   デフォルト: `4.0`   yマイナー目盛りの目盛りサイズ。

`yminorticksvisible`   デフォルト: `false`   y軸のマイナー目盛りが表示されるかどうかを制御します。

`yminortickwidth`   デフォルト: `1.0`   yマイナー目盛りの目盛り幅。

`ypankey`   デフォルト: `AbstractPlotting.Keyboard.y`   y方向のパンを制限するためのキー。

`ypanlock`   デフォルト: `false`   y方向のインタラクティブなパンをロックします。

`yrectzoom`   デフォルト: `true`   矩形ズームがy次元に影響を与えるかどうかを制御します。

`yreversed`   デフォルト: `false`   y軸が上方向（false）または下方向（true）に進むかどうかを制御します。

`yscale`   デフォルト: `identity`   y軸のスケール。

`ytickalign`   デフォルト: `0.0`   軸スパインに対するytickマークの整列（0 = 外側、1 = 内側）。

`ytickcolor`   デフォルト: `RGBf0(0, 0, 0)`   ytickマークの色。

`ytickformat`   デフォルト: `AbstractPlotting.automatic`   yticksのフォーマット。

`yticklabelalign`   デフォルト: `AbstractPlotting.automatic`   yticklabelsの水平および垂直整列。

`yticklabelcolor`   デフォルト: `lift_parent_attribute(scene, :textcolor, :black)`   yticklabelsの色。

`yticklabelfont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   yticklabelsのフォントファミリー。

`yticklabelpad`   デフォルト: `4.0`   yticksとyticklabelsの間のスペース。

`yticklabelrotation`   デフォルト: `0.0`   yticklabelsの反時計回りの回転（ラジアン）。

`yticklabelsize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)`   yticklabelsのフォントサイズ。

`yticklabelspace`   デフォルト: `AbstractPlotting.automatic`   yticklabelsのために予約されたスペース。

`yticklabelsvisible`   デフォルト: `true`   yticklabelsが表示されるかどうかを制御します。

`yticks`   デフォルト: `AbstractPlotting.automatic`   yticks。

`yticksize`   デフォルト: `6.0`   ytickマークのサイズ。

`yticksvisible`   デフォルト: `true`   ytickマークが表示されるかどうかを制御します。

`ytickwidth`   デフォルト: `1.0`   ytickマークの幅。

`ytrimspine`   デフォルト: `false`   yスパインが最も外側の目盛りに制限されるかどうかを制御します。

`yzoomkey`   デフォルト: `AbstractPlotting.Keyboard.y`   y方向のズームを制限するためのキー。

`yzoomlock`   デフォルト: `false`   y方向のインタラクティブなズームをロックします。
