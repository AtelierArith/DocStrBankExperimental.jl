```
LMenu(parent::Scene; bbox = nothing, kwargs...)
```

複数の選択可能なオプションを持つドロップダウンメニューを作成します。キーワード引数 `options` を使用してオプションを渡すことができます。オプションは要素のイテラブルとして与えられます。各要素について、メニュー内のオプションラベルは `optionstring(element)` で決定され、オプション値は `optionvalue(element)` で決定されます。これらの関数はカスタムタイプのためにオーバーロードできます。デフォルトでは、`AbstractStrings` である要素はラベルと値の両方として扱われ、他のすべての要素は2つのエントリを持つことが期待されます。最初のエントリがラベルで、2番目のエントリが値です。

メニューでアイテムが選択されると、メニューの `selection` 属性は `optionvalue(selected_element)` に設定されます。

メニューが下部のシーン境界に近い場合、オープン方向を `direction = :up` に変更できます。

# 例

文字列エントリのメニュー:

```julia
menu1 = LMenu(scene, options = ["first", "second", "third"])
```

2要素エントリ、ラベルと関数のメニュー:

```julia
funcs = [sin, cos, tan]
labels = ["Sine", "Cosine", "Tangens"]

menu2 = LMenu(scene, options = zip(labels, funcs))
```

選択値のリフティング:

```julia
on(menu2.selection) do func
    # 選択された関数で何かをする
end
```

LMenu には以下の属性があります:

`alignmode`   デフォルト: `Inside()`   メニューの提案されたバウンディングボックス内での整列。

`cell_color_active`   デフォルト: `COLOR_ACCENT[]`   アクティブなときのセルの色

`cell_color_hover`   デフォルト: `COLOR_ACCENT_DIMMED[]`   ホバー時のセルの色

`cell_color_inactive_even`   デフォルト: `RGBf0(0.97, 0.97, 0.97)`   非アクティブな偶数のときのセルの色

`cell_color_inactive_odd`   デフォルト: `RGBf0(0.97, 0.97, 0.97)`   非アクティブな奇数のときのセルの色

`direction`   デフォルト: `:down`   メニューのオープニング方向 (:up または :down)

`dropdown_arrow_color`   デフォルト: `(:black, 0.2)`   ドロップダウン矢印の色

`dropdown_arrow_size`   デフォルト: `12px`   ドロップダウン矢印のサイズ

`halign`   デフォルト: `:center`   メニューの提案されたバウンディングボックス内での水平整列。

`height`   デフォルト: `Auto()`   メニューの高さ設定。

`i_selected`   デフォルト: `1`   選択されたアイテムのインデックス

`is_open`   デフォルト: `false`   メニューが利用可能なオプションを表示しているかどうか

`options`   デフォルト: `["no options"]`   メニューで選択可能なオプションのリスト。これは文字列と1つの文字列と1つの他の値を持つコンテナの混合の任意のイテラブルであることができます。エントリが単なる文字列の場合、その文字列はラベルと選択の両方です。エントリが1つの文字列と1つの他の値を持つコンテナの場合、文字列がラベルで、他の値が選択です。

`selection`   デフォルト: `nothing`   選択されたアイテムの値

`selection_cell_color_inactive`   デフォルト: `RGBf0(0.94, 0.94, 0.94)`   非アクティブなときの選択セルの色

`tellheight`   デフォルト: `true`   親レイアウトがこの要素の高さに調整できるかどうかを制御します

`tellwidth`   デフォルト: `true`   親レイアウトがこの要素の幅に調整できるかどうかを制御します

`textcolor`   デフォルト: `:black`   エントリテキストの色

`textpadding`   デフォルト: `(10, 10, 10, 10)`   エントリテキストのパディング

`textsize`   デフォルト: `20`   セルテキストのフォントサイズ

`valign`   デフォルト: `:center`   メニューの提案されたバウンディングボックス内での垂直整列。

`width`   デフォルト: `nothing`   メニューの幅設定。
