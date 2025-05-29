```
StylableSlider(
    range::AbstractVector;
    value=first(range),
    slider_height=15,
    thumb_width=slider_height,
    thumb_height=slider_height,
    track_height=slider_height / 2,
    track_active_height=track_height + 2,
    backgroundcolor="transparent",
    track_color="#eee",
    track_active_color="#ddd",
    thumb_color="#fff",
    style::Styles=Styles(),
    track_style::Styles=Styles(),
    thumb_style::Styles=Styles(),
    track_active_style::Styles=Styles(),
)

カスタマイズ可能な基本属性をキーワード引数を介して簡単に設定できるStylable Sliderを作成しますが、より高度な詳細は、CSSの全機能を使用して`style`、`track_style`、`thumb_style`、および`track_active_style`引数を介してスタイル設定できます。これは`<input type="range">`を使用せず、ネイティブスライダーをクロスブラウザ方式でスタイル設定することが容易ではないため、`<div>`とJavaScriptを使用したカスタム実装です。純粋なHTMLスライダーを使用する場合は、`Bonito.Slider`を使用してください。

# 例

```

@example App() do     Bonito.StylableSlider(         1:10;         value=5,         slider*height=20,         track*color="lightblue",         track*active*color="#F0F8FF",         thumb*color="#fff",         style=Styles(             CSS("hover", "background-color" => "lightgray"),             CSS("border-radius" => "0px"),         ),         track*style=Styles(             "border-radius" => "3px",             "border" => "1px solid black",         ),         thumb_style=Styles(             "border-radius" => "3px",             "border" => "1px solid black",         ),     ) end

```
