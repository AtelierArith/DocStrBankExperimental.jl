**`Makie.Menu <: Block`**

複数の選択可能なオプションを持つドロップダウンメニューです。キーワード引数 `options` を使ってオプションを渡すことができます。

オプションは要素のイテラブルとして与えられます。各要素について、メニュー内のオプションラベルは `optionlabel(element)` で決定され、オプション値は `optionvalue(element)` で決定されます。これらの関数はカスタムタイプのためにオーバーロードすることができます。デフォルトでは、2つの要素からなるタプルがラベルと値として期待され、`string(label)` がラベルとして使用されます。一方、他のすべてのオブジェクトに対しては、ラベル = `string(object)` および値 = object となります。

メニューでアイテムが選択されると、メニューの `selection` 属性は `optionvalue(selected_element)` に設定されます。何も選択されていない場合、その値は `nothing` です。

初期選択を設定するには、`default` キーワードを使ってラベルの1つを渡すことができます。

## コンストラクタ

```julia
Menu(fig_or_scene; default = nothing, kwargs...)
```

## 例

文字列エントリのメニュー、2番目が事前選択されている:

```julia
menu1 = Menu(fig[1, 1], options = ["first", "second", "third"], default = "second")
```

2要素エントリのメニュー、ラベルと関数:

```julia
funcs = [sin, cos, tan]
labels = ["Sine", "Cosine", "Tangens"]

menu2 = Menu(fig[1, 1], options = zip(labels, funcs))
```

選択が行われたときに関数を実行する:

```julia
on(menu2.selection) do selected_function
    # 選択された関数で何かをする
end
```

**属性**

(`?Makie.Menu.x` を REPL で入力すると属性 `x` についての詳細情報が得られます)

`alignmode`, `cell_color_active`, `cell_color_hover`, `cell_color_inactive_even`, `cell_color_inactive_odd`, `direction`, `dropdown_arrow_color`, `dropdown_arrow_size`, `fontsize`, `halign`, `height`, `i_selected`, `is_open`, `options`, `prompt`, `scroll_speed`, `selection`, `selection_cell_color_inactive`, `tellheight`, `tellwidth`, `textcolor`, `textpadding`, `valign`, `width`
