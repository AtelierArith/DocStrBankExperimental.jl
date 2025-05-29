IntervalSlider には以下の属性があります：

`alignmode`   デフォルト: `Inside()`   スライダーの親 GridLayout における整列モード。

`color_active`   デフォルト: `COLOR_ACCENT[]`   マウスがスライダーをクリックしてドラッグしているときのスライダーの色。

`color_active_dimmed`   デフォルト: `COLOR_ACCENT_DIMMED[]`   マウスがスライダーの上にホバーしているときのスライダーの色。

`color_inactive`   デフォルト: `RGBf0(0.94, 0.94, 0.94)`   スライダーが操作されていないときの色。

`halign`   デフォルト: `:center`   提案されたバウンディングボックス内でのスライダーの水平整列。

`height`   デフォルト: `Auto()`   スライダーの高さ設定。

`horizontal`   デフォルト: `true`   スライダーが水平指向かどうかを制御します。

`interval`   デフォルト: `(0, 0)`   スライダーの現在の区間。これを手動で設定しないでください。`set_close_to!` 関数を使用してください。

`linewidth`   デフォルト: `15`   スライダーラインの幅。

`range`   デフォルト: `0:0.01:10`   スライダーが選択できる値の範囲。

`snap`   デフォルト: `true`   ボタンが有効な位置にスナップするか、自由に移動するかを制御します。

`startvalues`   デフォルト: `AbstractPlotting.automatic`   スライダーの開始値またはスライダー範囲内で最も近い値。

`tellheight`   デフォルト: `true`   親レイアウトがこの要素の高さに調整できるかどうかを制御します。

`tellwidth`   デフォルト: `true`   親レイアウトがこの要素の幅に調整できるかどうかを制御します。

`valign`   デフォルト: `:center`   提案されたバウンディングボックス内でのスライダーの垂直整列。

`width`   デフォルト: `Auto()`   スライダーの幅設定。
