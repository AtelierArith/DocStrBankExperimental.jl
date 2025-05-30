```
Editable(x::Real; [prefix, suffix, format])
```

PlutoUIの[`Scrubbable`](@ref)に似たPlutoウィジェットを作成しますが、入力として任意の（Real）数値を含むことができます。

表示されるHTMLは、青い背景のspanを作成し、その中に数値が含まれ、オプションのテキスト`prefix`とオプションのテキスト`suffix`が前に配置されます。`format`が指定されている場合、表示される数値のフォーマットには[d3-format](https://github.com/d3/d3-format#locale_format)仕様が使用されます。

ウィジェットは、Enterキーを押すか、ウィジェット自体からフォーカスを移動させたときのみ、ボンドの更新をトリガーします。

![79f77981-2c53-4ff0-bd13-8213519e0bca](https://github.com/disberd/PlutoExtras.jl/assets/12846528/cb0f19e3-7dcb-46d6-88b1-1bbe1592dd1c)

# キーワード引数

  * `prefix::AbstractString`: 表示されるHTMLで数値の前に挿入される文字列。サフィックスをクリックすると、数値を定義する全テキストが選択されます
  * `suffix::AbstractString`: 表示されるHTMLで数値の後に挿入される文字列。サフィックスをクリックすると、数値を定義する全テキストが選択されます
  * `format::AbstractString`: HTMLで数値を表示するために使用するフォーマットを指定する文字列。[d3-format](https://github.com/d3/d3-format#locale_format)仕様を使用します
