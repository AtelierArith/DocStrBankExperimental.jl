```
Menu(parent::Scene; bbox = nothing, kwargs...)
```

複数の選択可能なオプションを持つドロップダウンメニューを作成します。オプションはキーワード引数 `options` で渡すことができます。オプションは要素のイテラブルとして与えられます。各要素について、メニュー内のオプションラベルは `optionlabel(element)` で決定され、オプション値は `optionvalue(element)` で決定されます。これらの関数はカスタムタイプのためにオーバーロードすることができます。デフォルトでは、2つの要素からなるタプルがラベルと値として期待され、`string(label)` がラベルとして使用されますが、他のすべてのオブジェクトについては、ラベル = `string(object)` および値 = object となります。

メニューでアイテムが選択されると、メニューの `selection` 属性は `optionvalue(selected_element)` に設定されます。

メニューが下部のシーン境界に近い場合、オープン方向を `direction = :up` に変更できます。

# 例

文字列エントリのメニュー:

```julia
menu1 = Menu(scene, options = ["first", "second", "third"])
```

2要素エントリ、ラベルと関数のメニュー:

```julia
funcs = [sin, cos, tan]
labels = ["Sine", "Cosine", "Tangens"]

menu2 = Menu(scene, options = zip(labels, funcs))
```

選択値のリフティング:

```julia
on(menu2.selection) do func
    # 選択された関数で何かをする
end
```

メニューには以下の属性があります:

`alignmode`   デフォルト: `Inside()`   メニューの提案されたバウンディングボックス内での整列。

`cell_color_active`   デフォルト: `COLOR_ACCENT[]`   アクティブ時のセルの色

`cell_color_hover`   デフォルト: `COLOR_ACCENT_DIMMED[]`   ホバー時のセルの色

`cell_color_inactive_even`   デフォルト: `RGBf0(0.97, 0.97, 0.97)`   非アクティブ時の偶数セルの色

`cell_color_inactive_odd`   デフォルト: `RGBf0(0.97, 0.97, 0.97)`   非アクティブ時の奇数セルの色

`direction`   デフォルト: `:down`   メニューのオープン方向 (:up または :down)

`dropdown_arrow_color`   デフォルト: `(:black, 0.2)`   ドロップダウン矢印の色

`dropdown_arrow_size`   デフォルト: `12px`   ドロップダウン矢印のサイズ

`halign`   デフォルト: `:center`   提案されたバウンディングボックス内でのメニューの水平整列。

`height`   デフォルト: `Auto()`   メニューの高さ設定。

`i_selected`   デフォルト: `0`   選択されたアイテムのインデックス

`is_open`   デフォルト: `false`   メニューが利用可能なオプションを表示しているかどうか

`options`   デフォルト: `["no options"]`   メニューで選択可能なオプションのリスト。これは、文字列と1つの文字列および1つの他の値を持つコンテナの混合の任意のイテラブルであることができます。エントリが単なる文字列の場合、その文字列はラベルと選択の両方です。エントリが1つの文字列と1つの他の値を持つコンテナの場合、文字列がラベルで、他の値が選択となります。

`prompt`   デフォルト: `"Select..."`   i == 0 のときに選択を促すデフォルトメッセージ

`selection`   デフォルト: `nothing`   選択されたアイテムの値

`selection_cell_color_inactive`   デフォルト: `RGBf0(0.94, 0.94, 0.94)`   非アクティブ時の選択セルの色

`tellheight`   デフォルト: `true`   親レイアウトがこの要素の高さに調整できるかどうかを制御します

`tellwidth`   デフォルト: `true`   親レイアウトがこの要素の幅に調整できるかどうかを制御します

`textcolor`   デフォルト: `:black`   エントリテキストの色

`textpadding`   デフォルト: `(10, 10, 10, 10)`   エントリテキストのパディング

`textsize`   デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)`   セルテキストのフォントサイズ

`valign`   デフォルト: `:center`   提案されたバウンディングボックス内でのメニューの垂直整列。

`width`   デフォルト: `nothing`   メニューの幅設定。 ```
