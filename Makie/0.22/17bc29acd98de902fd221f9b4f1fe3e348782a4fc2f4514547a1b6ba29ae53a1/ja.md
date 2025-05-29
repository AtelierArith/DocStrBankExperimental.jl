**`Makie.SliderGrid <: Block`**

1つ以上の水平`Slider`のグリッドで、各スライダーの左側には名前ラベルがあり、右側には値ラベルがあります。

渡す`NamedTuple`は1つの`Slider`を指定します。常に`range`と`label`を渡す必要があり、オプションで値ラベルのための`format`を指定できます。それ以外にも、`startvalue`のように`Slider`が受け取る任意のキーワードを設定できます。

`format`キーワードは、Format.jlスタイルの`String`（例: "{:.2f}Hz"）や関数であることができます。

## コンストラクタ

```julia
SliderGrid(fig_or_scene, nts::NamedTuple...; kwargs...)
```

## 例

```julia
sg = SliderGrid(fig[1, 1],
    (label = "Amplitude", range = 0:0.1:10, startvalue = 5),
    (label = "Frequency", range = 0:0.5:50, format = "{:.1f}Hz", startvalue = 10),
    (label = "Phase", range = 0:0.01:2pi,
        format = x -> string(round(x/pi, digits = 2), "π"))
)
```

スライダーの値を扱う:

```julia
on(sg.sliders[1].value) do val
    # `val`を使って何かをする
end
```

**属性**

(REPLで`?Makie.SliderGrid.x`と入力すると、属性`x`に関する詳細情報が得られます)

`alignmode`, `halign`, `height`, `tellheight`, `tellwidth`, `valign`, `value_column_width`, `width`
