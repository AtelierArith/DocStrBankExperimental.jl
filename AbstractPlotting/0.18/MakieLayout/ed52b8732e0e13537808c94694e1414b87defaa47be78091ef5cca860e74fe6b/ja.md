Axis3には以下の属性があります：

`alignmode`   デフォルト: `Inside()`   シーンの提案されたバウンディングボックス内での整列。

`aspect`   デフォルト: `(1, 1, 2 / 3)`   3つの軸の相互のアスペクト。

`azimuth`   デフォルト: `1.275pi`   カメラの方位角。

`backgroundcolor`   デフォルト: `:transparent`   背景色。

`elevation`   デフォルト: `pi / 8`   カメラの高度角。

`halign`   デフォルト: `:center`   シーンの提案されたバウンディングボックス内での水平整列。

`height`   デフォルト: `nothing`   シーンの高さ設定。

`limits`   デフォルト: `(nothing, nothing, nothing)`   ユーザーが手動で設定した制限。`reset_limits!`を呼び出すと再設定され、`autolimits!`によってnothingに設定されます。タプル(xlow, xhigh, ylow, high, zlow, zhigh)またはタプル(nothing*or*xlims, nothing*or*ylims, nothing*or*zlims)のいずれかです。`xlims!`、`ylims!`、`zlims!`および`limits!`によって設定されます。

`palette`   デフォルト: `if scene !== nothing && haskey(scene.attributes, :palette)     deepcopy(scene.palette) else     Attributes() end`   キーごとに1つのパレットを持つ属性、例えば`color = [:red, :green, :blue]`。

`perspectiveness`   デフォルト: `0.0`   0から1の間の数値で、0は正投影、1は完全な透視。

`protrusions`   デフォルト: `30`   軸の側面の突起、ラベルなどのために予約された隙間の量。

`targetlimits`   デフォルト: `FRect3D(Vec3f0(0, 0, 0), Vec3f0(1, 1, 1))`   他の制約（アスペクトなど）に基づいて軸が設定しようとする制限。これを直接設定しないでください。代わりに`xlims!`、`ylims!`または`limits!`を使用してください。

`tellheight`   デフォルト: `true`   親レイアウトがこの要素の高さに調整できるかどうかを制御します。

`tellwidth`   デフォルト: `true`   親レイアウトがこの要素の幅に調整できるかどうかを制御します。

`title`   デフォルト: `""`   軸のタイトル文字列。

`titlealign`   デフォルト: `:center`   タイトルの水平整列。

`titlecolor`   デフォルト: `lift_parent_attribute(scene, :textcolor, :black)`   タイトルの色。

`titlefont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   タイトルのフォントファミリー。

`titlegap`   デフォルト: `4.0`   軸とタイトルの間の隙間。

`titlesize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)`   タイトルのフォントサイズ。

`titlevisible`   デフォルト: `true`   タイトルが表示されるかどうかを制御します。

`valign`   デフォルト: `:center`   シーンの提案されたバウンディングボックス内での垂直整列。

`viewmode`   デフォルト: `:fitzoom`   最終的な投影に影響を与えるビュー モード。`:fit`は、制限を常にビューポートにフィットさせる投影を生成し、回転に対して不変です。`:fitzoom`はx/y比を保持しますが、コーナーがシーンのビューポートに触れるようにビューを引き伸ばします。`:stretch`は、ビューポートを埋めるためにx方向とy方向の両方で別々にスケーリングし、設定された`aspect`を歪める可能性があります。

`width`   デフォルト: `nothing`   シーンの幅設定。

`xautolimitmargin`   デフォルト: `(0.05, 0.05)`   x方向の自動制限に追加される相対的なマージン。

`xgridcolor`   デフォルト: `:gray80`   xグリッドの色。

`xgridvisible`   デフォルト: `true`   xグリッドが表示されるかどうかを制御します。

`xlabel`   デフォルト: `"x"`   xラベル。

`xlabelalign`   デフォルト: `AbstractPlotting.automatic`   xラベルの整列。

`xlabelcolor`   デフォルト: `lift_parent_attribute(scene, :textcolor, :black)`   xラベルの色。

`xlabelfont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   xラベルのフォント。

`xlabeloffset`   デフォルト: `40`   xラベルのオフセット。

`xlabelrotation`   デフォルト: `AbstractPlotting.automatic`   xラベルの回転。

`xlabelsize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)`   xラベルのサイズ。

`xlabelvisible`   デフォルト: `true`   xラベルが表示されるかどうかを制御します。

`xspinecolor`   デフォルト: `:black`   xスパインの色。

`xspinesvisible`   デフォルト: `true`   xスパインが表示されるかどうかを制御します。

`xspinewidth`   デフォルト: `1`   xスパインの幅。

`xtickcolor`   デフォルト: `:black`   xティックの色。

`xtickformat`   デフォルト: `AbstractPlotting.automatic`   xティックのフォーマット。

`xticklabelcolor`   デフォルト: `lift_parent_attribute(scene, :textcolor, :black)`   xティックラベルの色。

`xticklabelfont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   xティックラベルのフォント。

`xticklabelsize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)`   xティックラベルのサイズ。

`xticklabelsvisible`   デフォルト: `true`   xティックラベルが表示されるかどうかを制御します。

`xticks`   デフォルト: `WilkinsonTicks(5; k_min = 3)`   xティック。

`xticksvisible`   デフォルト: `true`   xティックが表示されるかどうかを制御します。

`xtickwidth`   デフォルト: `1`   xティックの幅。

`xypanelcolor`   デフォルト: `:transparent`   xyパネルの色。

`xypanelvisible`   デフォルト: `true`   xyパネルが表示されるかどうかを制御します。

`xzpanelcolor`   デフォルト: `:transparent`   xzパネルの色。

`xzpanelvisible`   デフォルト: `true`   xzパネルが表示されるかどうかを制御します。

`yautolimitmargin`   デフォルト: `(0.05, 0.05)`   y方向の自動制限に追加される相対的なマージン。

`ygridcolor`   デフォルト: `:gray80`   yグリッドの色。

`ygridvisible`   デフォルト: `true`   yグリッドが表示されるかどうかを制御します。

`ylabel`   デフォルト: `"y"`   yラベル。

`ylabelalign`   デフォルト: `AbstractPlotting.automatic`   yラベルの整列。

`ylabelcolor`   デフォルト: `lift_parent_attribute(scene, :textcolor, :black)`   yラベルの色。

`ylabelfont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   yラベルのフォント。

`ylabeloffset`   デフォルト: `40`   yラベルのオフセット。

`ylabelrotation`   デフォルト: `AbstractPlotting.automatic`   yラベルの回転。

`ylabelsize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)`   yラベルのサイズ。

`ylabelvisible`   デフォルト: `true`   yラベルが表示されるかどうかを制御します。

`yspinecolor`   デフォルト: `:black`   yスパインの色。

`yspinesvisible`   デフォルト: `true`   yスパインが表示されるかどうかを制御します。

`yspinewidth`   デフォルト: `1`   yスパインの幅。

`ytickcolor`   デフォルト: `:black`   yティックの色。

`ytickformat`   デフォルト: `AbstractPlotting.automatic`   yティックのフォーマット。

`yticklabelcolor`   デフォルト: `lift_parent_attribute(scene, :textcolor, :black)`   yティックラベルの色。

`yticklabelfont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   yティックラベルのフォント。

`yticklabelsize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)`   yティックラベルのサイズ。

`yticklabelsvisible`   デフォルト: `true`   yティックラベルが表示されるかどうかを制御します。

`yticks`   デフォルト: `WilkinsonTicks(5; k_min = 3)`   yティック。

`yticksvisible`   デフォルト: `true`   yティックが表示されるかどうかを制御します。

`ytickwidth`   デフォルト: `1`   yティックの幅。

`yzpanelcolor`   デフォルト: `:transparent`   yzパネルの色。

`yzpanelvisible`   デフォルト: `true`   yzパネルが表示されるかどうかを制御します。

`zautolimitmargin`   デフォルト: `(0.05, 0.05)`   z方向の自動制限に追加される相対的なマージン。

`zgridcolor`   デフォルト: `:gray80`   zグリッドの色。

`zgridvisible`   デフォルト: `true`   zグリッドが表示されるかどうかを制御します。

`zlabel`   デフォルト: `"z"`   zラベル。

`zlabelalign`   デフォルト: `AbstractPlotting.automatic`   zラベルの整列。

`zlabelcolor`   デフォルト: `lift_parent_attribute(scene, :textcolor, :black)`   zラベルの色。

`zlabelfont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   zラベルのフォント。

`zlabeloffset`   デフォルト: `50`   zラベルのオフセット。

`zlabelrotation`   デフォルト: `AbstractPlotting.automatic`   zラベルの回転。

`zlabelsize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)`   zラベルのサイズ。

`zlabelvisible`   デフォルト: `true`   zラベルが表示されるかどうかを制御します。

`zspinecolor`   デフォルト: `:black`   zスパインの色。

`zspinesvisible`   デフォルト: `true`   zスパインが表示されるかどうかを制御します。

`zspinewidth`   デフォルト: `1`   zスパインの幅。

`ztickcolor`   デフォルト: `:black`   zティックの色。

`ztickformat`   デフォルト: `AbstractPlotting.automatic`   zティックのフォーマット。

`zticklabelcolor`   デフォルト: `lift_parent_attribute(scene, :textcolor, :black)`   zティックラベルの色。

`zticklabelfont`   デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")`   zティックラベルのフォント。

`zticklabelsize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)`   zティックラベルのサイズ。

`zticklabelsvisible`   デフォルト: `true`   zティックラベルが表示されるかどうかを制御します。

`zticks`   デフォルト: `WilkinsonTicks(5; k_min = 3)`   zティック。

`zticksvisible`   デフォルト: `true`   zティックが表示されるかどうかを制御します。

`ztickwidth`   デフォルト: `1`   zティックの幅。
