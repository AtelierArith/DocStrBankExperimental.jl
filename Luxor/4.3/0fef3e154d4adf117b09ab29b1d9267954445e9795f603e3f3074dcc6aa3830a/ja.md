```
textformat(e1, e2, e3...;
    color=getcolor(),
    fontsize=get_fontsize(),
    fontface="Helvetica",
    leading=120,
    baseline=0,
    prolog=nothing,
    advance=1.0,
    position=Point(0, 0),
    width=300)
```

要素 `e1`, `e2`, ... にテキストを描画します。各要素は次のいずれかです：

  * 文字列
  * テキストとフォーマットパラメータを含む名前付きタプル：

テキストは `position` から始まり、`width` によって制約されます。

名前付きタプルの要素は次のようになります：

```julia
(
    text= "a string",
    color = "blue",
    fontsize = 12,
    fontface = "JuliaMono-Italic",
    leading = 100,
    baseline = 0,
    advance = 1.0,
    prolog = nothing
)
```

`advance` が 1.0 の場合、要素はスペースで区切られます。それ以外の場合は `advance` 単位（正のシフトは右に）で区切られます。

`baseline` は通常 0 ですが、正の値はテキストを上に移動させます。

`leading` はここではフォントサイズに対するパーセンテージであり、デフォルトは 120% です。

`prolog` は引数 `(position::Point, str::String)` を持つ関数を呼び出し、テキストが描画される前に呼び出されます。

次のテキストが配置されるポイントを返します。

この関数は Toy テキスト API を使用します。

## 例

この例では、赤い太字の見出しと、その下にオレンジ色の等幅フォントの段落を描画します。

```julia
@draw begin
    background("black")
    fontsize(20)
    textformat(
        (text="Heading",
            fontface="AvenirNext-Heavy",
            fontsize=40,
            leading=100,
            color = "red",
        ),
        (text="The first paragraph.",
            fontface = "JuliaMono-Light",
            fontsize = 20,
            color="orange"
        ),
    position = boxtopleft() + (100, 100),
    width = 150
    )
end
```
