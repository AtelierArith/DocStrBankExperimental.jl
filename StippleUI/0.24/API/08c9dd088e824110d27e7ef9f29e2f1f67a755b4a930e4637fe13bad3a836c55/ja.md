```
`csscolors(name, color)`
`csscolors(names, colors)`
`csscolors(prefix, colors)`
```

クォーサー要素のスタイリングに使用する色を定義するcss文字列を構築します。これは、キーワード引数`color`の値として、またはそれぞれのプレフィックス`text-`または`bg-`を持つクラス名として使用されます。（参照：[quasar docs](https://quasar.dev/style/color-palette)）

# 使用法

css = style(csscolors(:stipple, [RGB(0.2, 0.4, 0.8), "#123456", RGBA(0.1, 0.2, 0.3, 0.5)]))

ui(model) = css * page(model, class="container, text-stipple-1", [   btn("Hit me", @click(:pressed), color="stipple-3") ])
