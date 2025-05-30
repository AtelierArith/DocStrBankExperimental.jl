```
Textbox(parent::Scene; bbox = nothing, kwargs...)
```

Textbox には以下の属性があります: `alignmode` デフォルト: `Inside()` 提案されたバウンディングボックス内のテキストボックスの配置。

`bordercolor` デフォルト: `RGBf0(0.8, 0.8, 0.8)` ボックスの境界線の色。

`bordercolor_focused` デフォルト: `COLOR_ACCENT[]` フォーカス時のボックスの境界線の色。

`bordercolor_focused_invalid` デフォルト: `RGBf0(1, 0, 0)` フォーカス時かつ無効な場合のボックスの境界線の色。

`bordercolor_hover` デフォルト: `COLOR_ACCENT_DIMMED[]` ホバー時のボックスの境界線の色。

`borderwidth` デフォルト: `2.0` ボックスの境界線の幅。

`boxcolor` デフォルト: `:transparent` ボックスの色。

`boxcolor_focused` デフォルト: `:transparent` フォーカス時のボックスの色。

`boxcolor_focused_invalid` デフォルト: `RGBAf0(1, 0, 0, 0.3)` フォーカス時のボックスの色。

`boxcolor_hover` デフォルト: `:transparent` ホバー時のボックスの色。

`cornerradius` デフォルト: `8` テキストボックスの角の半径。

`cornersegments` デフォルト: `20` 1つの丸い角のコーナーセグメント。

`cursorcolor` デフォルト: `:transparent` カーソルの色。

`defocus_on_submit` デフォルト: `true` 文字列が送信されたときにテキストボックスがフォーカスを外すかどうかを制御します。

`displayed_string` デフォルト: `nothing` 現在表示されている文字列（内部使用）。

`focused` デフォルト: `false` テキストボックスがフォーカスされており、テキスト入力を受け取るかどうか。

`font` デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")` フォントファミリー。

`halign` デフォルト: `:center` 提案されたバウンディングボックス内のテキストボックスの水平配置。

`height` デフォルト: `Auto()` テキストボックスの高さ設定。

`placeholder` デフォルト: `"Click to edit..."` 保存された文字列がないときに表示されるプレースホルダーテキスト。

`reset_on_defocus` デフォルト: `false` テキストボックスのフォーカスを外したときに表示されているテキストが保存されたテキストにリセットされるかどうかを制御します。

`restriction` デフォルト: `nothing` is_allowed(char, restriction)を介して許可されるUnicode入力を制限します。

`stored_string` デフォルト: `nothing` 現在保存されている文字列。

`tellheight` デフォルト: `true` 親レイアウトがこの要素の高さに調整できるかどうかを制御します。

`tellwidth` デフォルト: `true` 親レイアウトがこの要素の幅に調整できるかどうかを制御します。

`textcolor` デフォルト: `lift_parent_attribute(scene, :textcolor, :black)` テキストの色。

`textcolor_placeholder` デフォルト: `RGBf0(0.5, 0.5, 0.5)` プレースホルダーのテキストの色。

`textpadding` デフォルト: `(10, 10, 10, 10)` ボックスに対するテキストのパディング。

`textsize` デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)` テキストのサイズ。

`validator` デフォルト: `str->begin         #= /Users/atelierarith/.julia/packages/AbstractPlotting/2A5iv/src/makielayout/defaultattributes.jl:952 =#         true     end` 現在の文字列が有効かどうかを判断するためにvalidate_textbox(string, validator)で呼び出されるバリデーター。デフォルトでは、完全な文字列に一致する必要があるRegExまたは文字列を入力として受け取り、Boolを返す関数であることができます。バリデーターが型T（例えばFloat64）の場合、バリデーションは`tryparse(string, T)`になります。

`valign` デフォルト: `:center` 提案されたバウンディングボックス内のテキストボックスの垂直配置。

`width` デフォルト: `Auto()` テキストボックスの幅設定。
